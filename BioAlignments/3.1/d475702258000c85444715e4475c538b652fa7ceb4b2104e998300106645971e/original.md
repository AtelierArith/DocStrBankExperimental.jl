```
cigar(aln::Alignment)
```

Make a CIGAR string encoding of `aln`.

This is not entirely lossless as it discards the alignments start positions.
