```
printatom(atom::Atom)
printatom(io::IO, atom::Atom)
```

Prints an `Atom` structure in a human-readable format, with a title line. By default the output is printed to `stdout`, and the `io` argument can be used to specify a different output stream.

### Example

```jldoctest
julia> using PDBTools

julia> atoms = read_pdb(PDBTools.TESTPDB, "protein and residue 2");

julia> printatom(atoms[1])
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
      13    N     CYS     A        2        2   -6.351  -14.461   -5.695  1.00  0.00     1    PROT        13

julia> atoms[1] # default show method
   index name resname chain   resnum  residue        x        y        z occup  beta model segname index_pdb
      13    N     CYS     A        2        2   -6.351  -14.461   -5.695  1.00  0.00     1    PROT        13
```
