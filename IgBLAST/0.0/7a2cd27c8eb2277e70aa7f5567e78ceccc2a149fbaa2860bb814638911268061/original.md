```
IgBLAST
```

A Julia package for running IgBLAST analyses on immunoglobulin (Ig) and T cell receptor (TCR) sequences.

This package provides a convenient interface to install and run IgBLAST, supporting both IgBLASTn and IgBLASTp variants. It handles the installation of IgBLAST binaries, prepares input files, runs analyses, and monitors progress.

# Exports

  * `install_igblast`: Function to install IgBLAST binaries
  * `run_igblast`: Main function to run IgBLAST analyses
  * `is_igblast_installed`: Function to check if IgBLAST is installed
  * `IgBLASTn`: Type representing the nucleotide version of IgBLAST
  * `IgBLASTp`: Type representing the protein version of IgBLAST

# Examples

```julia
using IgBLAST

# Install IgBLAST if not already installed
install_igblast()

# Run an IgBLASTn analysis
run_igblast(
    IgBLASTn,
    "query.fasta",
    "V.fasta",
    "D.fasta",
    "J.fasta",
    "auxiliary.txt",
    "output.txt",
    additional_params = Dict("organism" => "human", "domain_system" => "imgt")
)
```
