```
sumblock(ex::String; Ts = 0, n = 1)
```

長さ `n` のベクトルを合計（または減算）するサマーノード（名前付き状態空間システム）を作成します。

# 引数:

  * `Ts`: サンプル時間
  * `n`: 入力および出力ベクトルの長さ。スカラーの場合は `n=1` に設定します。

`sumblock` を使用してブロックダイアグラムを形成する際には、`sumblock` から返されるシステムの入力名が式の右側に対応し、出力名が左側の変数に対応することに注意してください。したがって、接続リストでは通常 `:y => :y` のように接続をリストします。 [`connect`](@ref) 関数に接続します。使用例については、チュートリアルを参照してください。

  * https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/hinf_connection/
  * https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/api/#RobustAndOptimalControl.connect-Tuple{Any}

# 例:

```
julia> sumblock("uP = vf + yL")
NamedStateSpace{Continuous, Int64}
D = 
 1  1

With state  names: 
     input  names: vf yL
     output names: uP


julia> sumblock("x_diff = xr - xh"; n=3)
NamedStateSpace{Continuous, Int64}
D = 
 1  0  0  -1   0   0
 0  1  0   0  -1   0
 0  0  1   0   0  -1

With state  names: 
     input  names: xr1 xr2 xr3 xh1 xh2 xh3
     output names: x_diff1 x_diff2 x_diff3
     

julia> sumblock("a = b + c - d")
NamedStateSpace{Continuous, Int64}
D = 
 1  1  -1

With state  names: 
     input  names: b c d
     output names: a
```
