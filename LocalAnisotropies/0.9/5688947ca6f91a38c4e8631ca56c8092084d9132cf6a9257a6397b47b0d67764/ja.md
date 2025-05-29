```
convertangles(angles, convention1, convention2) # 角度を新しい角度に変換
convertangles(angles, convention1) # 角度をクォータニオンに変換
```

異なる規約間で角度を変換します。利用可能な回転規約については[`RotationRule`](@ref)のドキュメントを参照してください。

## 例

GSLIB規約からDatamine規約への3D回転[30, 30, 30]の変換

```julia
new_angs = convertangles([30,30,30], :GSLIB, :Datamine)
```
