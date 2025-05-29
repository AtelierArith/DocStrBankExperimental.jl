```
path = Path(dx, dy, dz)
```

Path構造体。このアクション（および`FlowPath`）では、動きは空間の各方向に対して1つずつの数値パラメータに基づいて定義されるのではなく、`Translate`、`Rotate`、および`HeartBeat`アクションのように定義されます。

このアクションでは、x（`dx`）、y（`dy`）、z（`dz`）の各スピンに対して独立して動きを定義する必要があります。`dx`、`dy`、`dz`は現在、各々が($N_{spins}* \times \; N_{discrete\,times}$)の3つの行列です。これは、各行が離散的な時間瞬間のセットに対するスピン軌道に対応することを意味します。

!!! note
    *`Flow`または`FlowPath`で動きを作成する際は、行列`dx`、`dy`、`dz`の行数が動きに影響を受けるスピンの数と一致することを確認する必要があります。

    動きに影響を受けるスピンの範囲は、`Motion`構造体の`spins`フィールドによって定義されます。

    例:

    ```julia-repl
    julia> motion = Motion(
        action = Path(
            dx=[0.01 0.02; 0.02 0.03],  # 2行
            dy=[0.02 0.03; 0.03 0.04], 
            dz=[0.03 0.04; 0.04 0.05]),
        time = TimeRange(0.0, 1.0),
        spins = SpinRange(1:2)          # 2スピン
    )
    ```


# 引数

  * `dx`: (`::AbstractArray{T<:Real}`, `[m]`) x方向の変位
  * `dy`: (`::AbstractArray{T<:Real}`, `[m]`) y方向の変位
  * `dz`: (`::AbstractArray{T<:Real}`, `[m]`) z方向の変位

# 戻り値

  * `path`: (`::Path`) Path構造体

# 例

```julia-repl
julia> path = Path(
           dx=[0.01 0.02; 0.02 0.03], 
           dy=[0.02 0.03; 0.03 0.04], 
           dz=[0.03 0.04; 0.04 0.05]
       )
```
