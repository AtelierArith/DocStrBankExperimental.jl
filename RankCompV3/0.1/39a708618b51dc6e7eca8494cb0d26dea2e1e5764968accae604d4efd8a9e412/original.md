```
reoa(fn_expr::AbstractString = "fn_expr.txt",
       fn_meta::AbstractString = "fn_meta.txt")
```

RankCompV3 is a differential expression analysis algorithm based on relative expression ordering (REO) of gene pairs. It can be applied to bulk or single-cell RNA-sequencing (scRNA-seq) data, microarray gene expression profiles and proteomics profiles, etc. When applied in scRNA-seq data, it can run in single-cell mode or pseudo-bulk mode. The pseudo-bulk mode is expected to improve the accuracy while decreasing runntime and memory cost. 

# Examples

## Quick Start

Run a test job with the input files distributed with the package.

```jldoctest
julia> using RankCompV3
# Use the default values for the following other parameters. If you need to modify the parameters, add them directly.
julia> result = reoa(use_testdata="yes")
```

The analysis results and a few plots will be generated and saved in the current work directory. They are also returned by the `reoa` function and can be captured by assign the returned values to a variable,  e.g., `result` in the above example.  

The first return value is a DataFrame, where rows are genes and columns are statistical values for each gene. All the genes passing the basic preprocessing step are retained. 

```jldoctest
julia> result
19999×2 DataFrame
   Row │ gene_name  group1_vs_group2
       │ Any        Any
───────┼─────────────────────────────
     1 │ DE1        up
     2 │ DE2        up
     3 │ DE3        up
     4 │ DE4        up
     5 │ DE5        up
     6 │ DE6        up
   ⋮   │     ⋮             ⋮
 19995 │ EE19996    up
 19996 │ EE19997    up
 19997 │ EE19998    up
 19998 │ EE19999    up
 19999 │ EE20000    up
                   19988 rows omitted
```

#### Run your own DEG analysis

You need to prepare two input files before the analysis: metadata file and expression matrix. `.rds`, `.csv`, `.txt`, `.tsv` and `.RData` files are supported. 

  * **metadata file (required).**

The metadata file contains at least two columns. The first column is the sample names, and the second column is the grouping information. Only two groups are supported at present, therefore, do not include more than two groups. 

Column names for a metadata should be `Name` and `Group`. 

See an example metadata file, [fn_meta.txt](https://github.com/yanjer/RankCompV3.jl/blob/master/test/fn_meta.txt).

  * **expression matrix file (required).**

The first column is the gene name and the column header should be `Name` and the rest columns are profiles for each cell or each sample. Each column header should be the sample name which appears in the metadata file.

See an example expression matrix file, [fn_expr.txt](https://github.com/yanjer/RankCompV3.jl/blob/master/test/fn_expr.txt).

Raw counts or expression values are recommended to use. Other values, e.g, FPKM, RPKM, TPM, log(counts) and log(normalized counts), can also be used, though normalization and batch effect removal are neither necessary nor recommended. 

Once the files are ready, you can carry out the DEG analysis with the default settings as follows. 

```jldoctest
julia> using RankCompV3
# Use the default values for the following other parameters. If you want to modify the parameters, add them directly.
julia> reoa("/public/yanj/data/fn_expr.txt",
	"/public/yanj/data/fn_metadata.txt")
```

Other parameters can be set by passing the value to the corresponding keyword. 

```jldoctest
julia> reoa("/public/yanj/data/fn_expr.txt",
    	"/public/yanj/data/fn_metadata.txt",
    	expr_threshold = 0,
    	min_profiles = 0,
    	min_features = 0,
    	pval_reo = 0.01,
     	pval_deg = 1.0,
     	padj_deg = 0.05,
    	use_pseudobulk = 0,
    	use_hk_genes = "yes"
    	hk_file = "HK_genes_info.tsv",
    	gene_name_type = "ENSEMBL",
    	ref_gene_max = 3000,
    	ref_gene_min = 100
    	n_iter = 128,
    	n_conv = 5,
    	work_dir = "./",
    	use_testdata = "no")
```
