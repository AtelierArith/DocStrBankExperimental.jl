```julia
load_alist(
    file_path;
    check_redundant,
    warn_unexpected_file_extension
)

```

Load an LDPC matrix from a text file in alist format. Returns a SparseMatrixCSC{Int8}.

By default, issues a warning if file extension is not ".alist". (Change `warn_unexpected_file_extension` to disable.) The alist format is redundant (the two halves of a file specify the same information, once by-row and once by-column). This function only uses the first half. (Change `check_redundant` to also parse and verify the second half.)

For definition of alist format, see http://www.inference.org.uk/mackay/codes/alist.html
