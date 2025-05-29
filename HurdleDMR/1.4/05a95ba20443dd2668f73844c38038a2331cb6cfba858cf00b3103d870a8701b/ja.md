```
fit(DMR,covars,counts; <キーワード引数>)
dmr(covars,counts; <キーワード引数>)
```

カウントに対する分散多項回帰（DMR）をフィットします。

DMRは、カウントの各列に対して独立したポアソンガンマラッソ回帰をフィットし、多項分布を近似し、各パスのセグメントを選択し、全体の多項分布の点推定を表す係数行列（DMRCoefsでラップされている）を返します（インターセプトが含まれている場合はそれも含まれます）。

# 例:

```julia
  m = fit(DMR,covars,counts)
```

# 引数

  * `covars` n-by-p の共変量の行列
  * `counts` n-by-d のカウントの行列（通常はスパース）

# キーワード

  * `intercept::Bool=false` 各ポアソンにインターセプトを含める
  * `parallel::Bool=true` ポアソンフィットを並列化する
  * `local_cluster::Bool=true` 単一のマルチコアマシンに適したメモリを共有するローカルクラスター モード、または、メモリの共有がコストのかかるマシン間で分散するのにより適したリモートクラスター モードを使用します。
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `select::SegSelect=MinAICc()` どのパスセグメントを選択するか
  * `kwargs...` fit(GammaLassoPath,...) に渡される追加のキーワード引数

```
