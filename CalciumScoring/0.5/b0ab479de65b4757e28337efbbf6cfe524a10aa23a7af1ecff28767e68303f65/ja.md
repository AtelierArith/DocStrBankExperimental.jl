## `Integrated`

```julia
function Integrated(
    vol, 
    I=sum(vol), 
    N=length(vol)
)
```

#### Inputs

  * vol: 関心領域
  * I: 全体の `vol` の統合強度
  * N: 全体の `vol` に含まれるボクセルの総数

#### References

[Integrated intensity-based technique for coronary artery calcium mass measurement: A phantom study](https://doi.org/10.1002/mp.16326)

[Accurate quantification of vessel cross-sectional area using CT angiography: a simulation study](https://doi.org/10.1007/s10554-016-1007-9)
