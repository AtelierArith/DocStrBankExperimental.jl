```
flowpath = FlowPath(dx, dy, dz, spin_reset)
```

FlowPath構造体。このアクションは`Path`と同じですが、`spin_reset`と呼ばれる追加のフィールドが含まれており、これはボリュームを離れるスピンを考慮し、別の入力位置に再マッピングされることを意味します。この場合、シミュレーション中にこれらのスピンの磁化状態をリセットする必要があります。

`dx`、`dy`、`dz`の行列と同様に、`spin_reset`のサイズは($N_{spins} \times \; N_{discrete\,times}$)です。

# 引数

  * `dx`: (`::AbstractArray{T<:Real}`, `[m]`) x方向の変位
  * `dy`: (`::AbstractArray{T<:Real}`, `[m]`) y方向の変位
  * `dz`: (`::AbstractArray{T<:Real}`, `[m]`) z方向の変位
  * `spin_reset`: (`::AbstractArray{Bool}`) スピン状態リセットフラグ

# 戻り値

  * `flowpath`: (`::FlowPath`) FlowPath構造体

# 例

```julia-repl
julia> flowpath = FlowPath(
           dx=[0.01 0.02; 0.02 0.03], 
           dy=[0.02 0.03; 0.03 0.04], 
           dz=[0.03 0.04; 0.04 -0.04],
           spin_reset=[false false; false true]
       )
```
