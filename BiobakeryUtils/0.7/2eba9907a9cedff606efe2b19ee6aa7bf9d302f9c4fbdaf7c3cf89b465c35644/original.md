```
write_pcl(infile; usemetadata=:all)
```

Writes a [PCL file](https://software.broadinstitute.org/cancer/software/gsea/wiki/index.php/Data_formats#PCL:_Stanford_cDNA_file_format_.28.2A.pcl.29) from a `CommunityProfile` with metadata attached to the samples.

`usemetadata` may be `:all`  or a vector of symbols.
