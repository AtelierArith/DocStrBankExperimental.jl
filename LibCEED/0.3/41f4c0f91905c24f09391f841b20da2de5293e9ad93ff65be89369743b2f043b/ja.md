```
CeedVector(c::Ceed, v2::AbstractVector; mtype=MEM_HOST, cmode=COPY_VALUES)
```

指定されたベクトル `v2` の内容を使用して新しい [`CeedVector`](@ref) を作成します。デフォルトでは、`v2` の内容が新しい [`CeedVector`](@ref) にコピーされますが、この動作は異なる `cmode` を指定することで変更できます。
