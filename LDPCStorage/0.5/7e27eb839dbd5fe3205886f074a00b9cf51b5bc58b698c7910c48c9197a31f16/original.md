```julia
load_ldpc_from_json(
    file_path;
    expand_qc_exponents_to_binary
)

```

Loads LDPC matrix from a json file containing compressed sparse column (CSC) storage for either of

  * `qccscjson` (CSC of quasi-cyclic exponents) format
  * `bincscjson` (CSC of sparse binary matrix) format

Use option to expand quasi-cyclic exponents and get a sparse binary matrix.
