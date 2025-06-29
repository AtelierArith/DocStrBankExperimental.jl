```
inv!(m::TaylorMap, m1::TaylorMap; dospin::Bool=true, work_ref::Union{Nothing,Vector{<:Union{Float64,ComplexF64}}}=nothing)
```

`TaylorMap`のインプレース逆数を計算し、`m = inv(m1)`を設定します。`m === m1`のエイリアスは許可されていますが、この場合、逆数を計算する前に`m1`のスカラー部分を格納するために一時ベクトルを使用する必要があります。これにより、マップの入口/出口座標を適切に処理できます。

### キーワード引数

  * `dospin` – クォータニオンも逆数を計算するかどうかを指定します。デフォルトは`true`です。
  * `work_ref` – `m === m1`の場合、一時ベクトルを使用してスカラー部分を格納する必要があります。提供されていない場合、`m === m1`のときにこの一時ベクトルは内部的に作成されます。デフォルトは`nothing`です。
