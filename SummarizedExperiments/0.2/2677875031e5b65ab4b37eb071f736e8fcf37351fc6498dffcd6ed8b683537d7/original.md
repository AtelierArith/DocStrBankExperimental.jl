The `SummarizedExperiment` class is a Bioconductor container for matrix-like data with annotations on the rows and columns. It is the data structure underlying analysis workflows for many genomics data modalities, ranging from microarrays, bulk and single-cell RNA sequencing, ChIP-seq, epigenomics and beyond.

Any number of arrays (also known as "assays") can be stored in the container,  provided they are assigned to unique names and all have the same extents for the first two dimensions. This reflects the fact that we often have multiple experimental readouts of the same shape, e.g., raw counts, normalized values, quality metrics. These assays are held as an `OrderedDict` so the order of their addition is respected.

The row and column annotations are stored as `DataFrame`s, with number of rows equal to the number of assay rows and columns, respectively. Any number and type of columns may be present in each `DataFrame`, with the only constraint being that the first column must be a `"name"` column of strings containing the feature/sample names. If no names are present, the `"name"` column must contain `nothing`s.

Each instance may also contain arbitrary metadata not associated with the rows or columns.
