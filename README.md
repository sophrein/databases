# Databases
This repository contains information pertaining to the communally-available databases present within `/hpc/groups/database` on the NHM HPC. All users will have read and execute privileges on all databases in the directory.


---


## Available databases
> - **Base path:** `/hpc/groups/database/`
> - Timestamp = download date
> - Size (GB) = uncompressed

### [NCBI BLAST](https://ftp.ncbi.nlm.nih.gov/blast/db/)
| Database | Timestamp | Path | Size |
| --- | --- | --- | --- |
| core_nt | 13-05-2026 | `BLAST/core_nt_{timestamp}/` | 283GB |
| mito | 14-05-2026 | `BLAST/mito_{timestamp}/` | 420MB |
| RefSeq representative Eukaryote Genomes | 14-05-2026 | `BLAST/ref_euk_rep_genomes_{timestamp}/` | 452GB |
| MIDORI2 unique CO1 | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_CO1/` | 698MB |
| MIDORI2 unique A6 (ATP6) | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_A6/` | 29.4MB |
| MIDORI2 unique A8 (ATP8) | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_A8/` | 12.4MB |
| MIDORI2 unique lrRNA (16S) | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_lrRNA/` | 157MB |
| MIDORI2 unique srRNA (12S) | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_srRNA/` | 74MB |
| MIDORI2 unique ND1 | 14-05-2026 | `MIDORI/MIDORI2_UNIQ_NUC_{release}_ND1/` | 40.9MB |

### [Kraken](https://benlangmead.github.io/aws-indexes/)
| Database | Timestamp | Path | Size |
| --- | --- | --- | --- |
| Kraken2 Standard | 14-05-2026 | `kraken/k2_standard_{release}/` | 97.3GB |
| Kraken2 plusPF | 14-05-2026 | `kraken/k2_pluspf_{release}/` | 103GB |
| Kraken2 NCBI | 24-09-2026 | `kraken/k2_NCBI_reference_{release}/` | XXXGB |


### [NCBI Taxonomy 'dump'](https://ftp.ncbi.nlm.nih.gov/pub/taxonomy/)
| Database | Timestamp | Path | Size |
| --- | --- | --- | --- |
| taxdump | 14-05-2026 | `ncbi_taxdump/taxdump_{timestamp}/` | 513MB |


---


## About the databases
- **core_nt**: Consists of GenBank+EMBL+DDBJ+PDB+RefSeq sequences, but excludes EST, STS, GSS, WGS, TSA, patent sequences as well as phase 0, 1, and 2 HTGS sequences and most eukaryotic chromosome sequences. The database is non-redundant. Identical sequences have been merged into one entry, while preserving the accession, GI, title and taxonomy information for each entry.
- **mito**: Complete or near-complete mitochondrial genome sequences from across the tree of life, and contained in either NCBI's RefSeq or GenBank databases.
- [**MIDORI2**](https://www.reference-midori.info/download.php): A curated mitochondrial reference database for taxonomic classification, derived from GenBank. 
    - 'unique': One sequence per species (unique haplotypes deduplicated to one per taxon).
    - 'total': All sequences retained, no deduplication.
    - 'raw': Unformatted FASTA with full taxonomy.
- **RefSeq representative Eukaryote Genomes**: Contains Reference genomes selected from the NCBI Refseq Genomes database. As a result, the genomes in this database are among the best quality genomes available at NCBI. It is also constructed with minimum redundancy in genome representation. For the eukaryotes, only one genome is included per organism. For other organisms, however, multiple genomes from diverse isolates of the same organism (such as E. coli) may be included.
- **kraken**: Databases formatted for use with kraken/Bracken, Kraken2, krakenUniq taxonomic Sequence Classifiers. Each database is built for 50, 75, 100, 150, 200, 250 and 300-mers.
    - 'Standard': Contains Refseq archaea, bacteria, viral, plasmid, human (not masked), and UniVec_Core.
    - 'plusPF': The standard kraken2 database, plus Refseq protozoa & fungi.
    - 'NCBI': Built from NCBI's curated reference and representative genome assemblies across all domains of life. Contains broader taxonomic coverage than the standard databases but with fewer bacterial strains.
- **Taxdump**: A structured, downloadable archive that provides the comprehensive taxonomic classification for all organisms in NCBI's database.


---


## Request a database
If you would like us to install a new database, or update an existing one to a new version, please get in touch with us at DNASeqFac@nhm.ac.uk

> Created 13-05-2026 by Dan Parsons.


---


## Decompression
You can decompress `.tar.gz` archives using the commands below. However, before you do please check whether the tool you're running can accept `.tar.gz` archives directly (as some can!).

To decompress the archive into a specified directory, run:
```
tar -xzvf {archive}.tar.gz -C /path/to/destination/{archive}/

-x: extract
-v: verbose (prints each file as it's extracted)
-f: filename follows
-C: extract to this directory (destination must already exist)
```

To first identify what is contained within a `.tar.gz` archive, and then decompress a specific file or directory from it, run:
```
tar -tzf {archive}.tar.gz          # find the path you want
tar -xzf {archive}.tar.gz path/to/found/{file.ext}   # extract just that file or directory

-t: list contents without extraction
-z: decompress with gzip
-f: filename follows
-z: decompress with gzip
```

To recompress back into a `.tar.gz` archive, run:
```
tar -czf {name_of_directory}.tar.gz> {name_of_directory}/

c: create a new archive
z: compress with gzip
f: filename follows
```
