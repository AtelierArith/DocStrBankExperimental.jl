```
qualify!(df::DataFrame; 
        lod = nothing, 
        loq = nothing, 
        lloq = nothing, 
        uloq = nothing, 
        lodsub = "<LOD", 
        loqsub = "<LOQ", 
        lloqsub = "<LLOQ", 
        uloqsub = ">ULOQ")
```

許容範囲外のデータを置き換えます。

  * `lod`: 検出限界; 値は「Data」で始まる列に合わせて昇格されます。
  * `loq`: 定量限界; 値は「Data」で始まる列に合わせて昇格されます。
  * `lloq`: 定量の下限; 値は「Data」で始まる列に合わせて昇格されます。
  * `uloq`: 定量の上限; 値は「Data」で始まる列に合わせて昇格されます。
  * `lodsub`: LOD未満の値の代替。
  * `loqsub`: LOQ未満の値の代替。
  * `lloqsub`: LLOQ未満の値の代替。
  * `uloqsub`: ULOQを超える値の代替。
