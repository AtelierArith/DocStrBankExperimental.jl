```
axesextend!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}, axisnumber::Integer; prepend::AbstractArray=[], append::AbstractArray=[])
```

選択した軸のパラメータ空間を、グリッドを前に追加し、後ろに追加することで拡張します。

解像度と単調性はチェックされないことに注意してください。

# 例

mdbm問題の第二パラメータを拡張する：

```jldoctest
julia> axesextend!(mymdbm,2,prepend=-6.2:0.05:-2.2,append=2.2:0.2:3);
```
