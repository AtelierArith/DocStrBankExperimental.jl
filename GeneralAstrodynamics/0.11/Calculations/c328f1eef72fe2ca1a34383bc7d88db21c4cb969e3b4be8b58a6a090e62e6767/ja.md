```julia
analyticalhalo(μ; Az, ϕ, steps, L, hemisphere)

```

`L`の周りのハロー軌道の解析解を返します。

**引数:** 

  * `μ`: CR3BPシステムの無次元質量パラメータ。
  * `Az`: ハロー軌道のための望ましい無次元Z振幅。
  * `ϕ`: 望ましいハロー軌道の位相。
  * `steps`: 返される状態の無次元時間点の数。
  * `L`: 軌道を描くラグランジュ点（L1またはL2）。
  * `hemisphere`: 北半球または南半球のハロー軌道を指定します。

**出力:**

  * 同期位置ベクトル `r::Array{<:AbstractFloat}`
  * 同期速度ベクトル `v::Array{<:Abstractfloat}`。
  * ハロー軌道の周期 `Τ`。
  * Lが`1`または`2`でない場合は`ArgumentError`をスローします。

**参考文献:**

  * [Rund, 2018](https://digitalcommons.calpoly.edu/theses/1853/).
