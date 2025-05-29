```
RectiGrid(dims::NamedTuple{Na}; executor=Serial(), header=ComradeBase.NoHeader(), posang=0.0)
RectiGrid(dims::NTuple{N, <:DimensionalData.Dimension}; executor=Serial(), header=ComradeBase.NoHeader(), posang=0.0)
```

`dims`の次元を持つ直交格子のグリッドを作成します。慣例として、最初の2つの次元は空間次元`X/U`と`Y/V`です。残りの次元は何でも可能で、例えば：

  * (:X, :Y, :Ti, :Fr)
  * (:X, :Y, :Fr, :Ti)
  * (:X, :Y) # 空間のみ

ここで、`X/U,Y/V`はそれぞれ画像/可視性空間におけるRAおよびDECの空間次元であり、`Ti`は時間次元、`Fr`は周波数次元です。

ほとんどの時間、ユーザーは単に[`imagepixels`](@ref)を呼び出して空間グリッドを作成すべきです。

## オプション引数

  * `executor`: 異なるモデルがどのように実行されるかを指定します。デフォルトは`Serial`で、これは直列CPU計算を意味します。スレッド計算を使用するには、[`ThreadsEx()`](@ref)を使用するか、`OhMyThreads.jl`をロードしてそのスケジューラを使用します。
  * `header`: グリッドの基礎となるヘッダー情報を指定します。これは、ソース、RAおよびDEC、MJDなどの画像に関する情報を保存するために使用されます。
  * `posang`: RA=0軸に対するグリッドの位置角を指定します。`posang != 0`のとき、XおよびY座標は回転したグリッドに対して相対的であり、空におけるRAおよびDECの向きとは異なります。空における真のポイントを見るには、`domainpoints(grid)`を呼び出してアクセスできます。

!!! warn
    `posang`引数とグリッド全体の回転は現在実験的であり、将来的にはマイナーリリースでも急に変更される可能性があります。


## 例

```julia
dims = RectiGrid((X(-5.0:0.1:5.0), Y(-4.0:0.1:4.0), Ti([1.0, 1.5, 1.75]), Fr([230, 345])); executor=ThreadsEx())
dims = RectiGrid((X = -5.0:0.1:5.0, Y = -4.0:0.1:4.0, Ti = [1.0, 1.5, 1.75], Fr = [230, 345]); executor=ThreadsEx()))
```
