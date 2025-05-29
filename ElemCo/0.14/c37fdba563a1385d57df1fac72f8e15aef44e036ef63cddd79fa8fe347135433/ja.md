```
@transform_ints(type="")
```

FCIDumpの積分を[`WfOptions.orb`](@ref ECInfos.WfOptions)を変換行列として使用して回転させます。

軌道は[`WfOptions.orb`](@ref ECInfos.WfOptions)から読み取られます。typeが[bo, BO, bi-orthogonal, Bi-orthogonal, biorth, biorthogonal, Biorthogonal]のいずれかである場合、双直交軌道が使用され、左の変換行列は[`WfOptions.orb`](@ref ECInfos.WfOptions)*[`WfOptions.left`](@ref ECInfos.WfOptions)から読み取られます。
