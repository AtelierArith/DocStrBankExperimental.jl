```julia
get_sample(pt)
get_sample(pt, chain)

```

`chain`オプションは省略可能で、デフォルトでは興味のある分布をターゲットとする最初のチェーンが使用されます（多くの場合、1つだけ、変分ケースでは2つになります）。
