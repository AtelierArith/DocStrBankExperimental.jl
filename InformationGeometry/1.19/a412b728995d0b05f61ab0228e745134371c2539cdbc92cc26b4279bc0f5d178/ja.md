```
SymbolicModel(DM::Union{AbstractDataModel,ModelMap}; sub::Bool=true)
```

可能であれば、モデルマップのための記号式の`String`を生成します。

キーワード引数`sub`は、与えられた変数名が`DM`から取得されるか（`sub=true`）、よりコピーしやすいように一般的な変数名（例：`θ[1]`）が使用されるか（`sub=false`）を制御します。
