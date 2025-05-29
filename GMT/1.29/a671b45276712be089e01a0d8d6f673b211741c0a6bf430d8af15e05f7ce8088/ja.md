```
Dout = whittaker(D::GMTdataset, lambda, d=2; weights=nothing)
```

または

```
z = whittaker(x::AbstractVecOrMat{<:Real}, y::VecOrMat{<:Real}, lambda, d=2; weights=nothing)
```

Whittaker-Henderson平滑化および補間を実行します。

### 引数

  * `D`:      `x,y`データ系列を持つGMTdataset。
  * `x,y`:    `D`形式の代わりに、`x`と`y`のベクトルを渡します。
  * `lambda`: 平滑化パラメータ；大きなlambdaはより滑らかな結果をもたらします。
  * `d`:      差分の次数（デフォルト = 2）。

### キーワード引数

  * `weights`: 重み（欠損データ/非欠損データのための0/1）。入力`y`にNaNが含まれている場合、別のフラグ値で置き換え、自動的に`w`を設定します。

### 引用

  * A Perfect Smoother (https://pubs.acs.org/doi/10.1021/ac034173t)
  * 'Smoothing and interpolation with finite differences'. Eilers P. H. C, 1994. (http://dl.acm.org/citation.cfm?id=180916)
  * 'A Perfect Smoother'からのMatlabコードをJuliaに翻訳。Paul H. C. Eilers. Analytical Chemistry 2003 75 (14), 3631-3636. DOI: 10.1021/ac034173t

### 例

```julia
D = gmtread(TESTSDIR * "/assets/nmr_with_weights_and_x.csv");
D2 = whittaker(D, 2e4, 2);
D3 = whittaker(D, 2e4, 3);
plot(D)
plot!(D2, lc=:red, lt=1, legend="Degree 2", plot=(data=D3, lc=:blue, lt=1, legend="Degree 3"), show=1)
```

```julia
t = 2001:0.003:2007;
_v = 5*cospi.((t .- 2000)/2); v = _v + (5*rand(length(t)) .- 2.5);
v[2002.6 .< t .< 2003.4] .= NaN;
z = whittaker(t, v, 0.01, 3);
plot(t, v, legend="Noisy", plot=(data=[t _v], lc=:green, lt=1, legend="Original"))
plot!(t, z, lc=:red, lt=1, legend="Degree 3", show=1)
```
