```
general_increment!(material::AbstractMaterial, dstrain_knowns::AbstractVector{Union{T, Missing}},
                   dstrain::AbstractVector{Union{T, Missing}}=dstrain_knowns,
                   max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

`material`に対して互換性のあるひずみ増分を見つけます。

材料の状態（`material.variables`）と*ひずみ*増分`dstrain_knowns`の非`missing`成分は、指定されたものとして扱われます。`missing`成分は解決されます。

このルーチンは、ひずみ増分の`missing`成分に対応する新しい応力状態の成分が、`material.variables.stress`に保存されている古い値のままになるように、ひずみ増分の`missing`成分を計算します。（実際には、これらの古い値はゼロに設定されることが多く、単軸引張試験や類似のシミュレーションを可能にします。）

「新しい」応力状態とは、材料を長さ`dt`の1タイムステップで積分した後の応力状態を意味します。

初期推定値`dstrain`の型は`AbstractVector{Union{T, Missing}}`であり、これはデフォルトでその型を持つ`dstrain_knowns`に設定できるようにするためです。初期推定値`dstrain`の`missing`成分は、ソルバーを呼び出す前にゼロに置き換えられます。

`find_dstrain!`を参照してください。
