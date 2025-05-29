```
eigen(t::AbstractTensor, (leftind, rightind)::Index2Tuple; kwargs...) -> D, V
```

テンソル `t` の固有値因子分解を、`rightind` から `leftind` への線形写像として計算します。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`eigen!(t)` を使用することで、`t` 内のデータが破壊/上書きされることを許可すると、より少ないメモリが割り当てられます。`eigen!` が呼び出される順列テンソルは、ドメインとコドメインが等しい必要があり、そうでない場合、固有値分解は無意味であり、次の式を満たすことはできません。

```
permute(t, (leftind, rightind)) * V = V * D
```

密行列の `eigen` と同じキーワード引数 `scale` と `permute` を受け入れます。詳細については、対応するドキュメントを参照してください。

`eig` と `eigh` も参照してください。
