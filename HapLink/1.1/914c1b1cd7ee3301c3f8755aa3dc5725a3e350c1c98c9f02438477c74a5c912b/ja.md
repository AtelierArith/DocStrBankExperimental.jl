```
Pseudoread(startpos::Integer, endpos::Integer, read::Haplotype)
Pseudoread(query::Union{SAM.Record,BAM.Record}, reference::NucleotideSeq)
```

参照配列に対する位置と違いによって表される、シーケンシングリード（実際のものまたは想像上のもの）のスタンドイン構造体です。
