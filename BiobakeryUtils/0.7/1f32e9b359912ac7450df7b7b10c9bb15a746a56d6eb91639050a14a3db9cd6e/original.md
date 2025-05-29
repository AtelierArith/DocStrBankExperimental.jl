```
read_pcl(infile; last_metadata=2)
```

Reads a [PCL file](https://software.broadinstitute.org/cancer/software/gsea/wiki/index.php/Data_formats#PCL:_Stanford_cDNA_file_format_.28.2A.pcl.29) and generates a `CommunityProfile` with metadata attached to the samples.

`last_metadata` may be a row number or a string representing the final metadatum.
