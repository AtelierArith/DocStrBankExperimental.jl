```
fit(HDMR,covars,counts; <キーワード引数>)
hdmr(covars,counts; <キーワード引数>)
```

カウントに対するハードル分布多項式回帰 (HDMR) をフィットします。

HDMRは、カウントの各列に独立したハードルラッソ回帰をフィットさせて多項式を近似し、各パスのセグメントを選択し、全体の多項式のポイント推定を表す係数行列（HDMRCoefsでラップ）を返します（インターセプトが含まれている場合はそれも含まれます）。

# 例:

```julia
  m = fit(HDMR,covars,counts)
```

# 引数

  * `covars` n-by-p の共変量行列
  * `counts` n-by-d のカウント行列（通常はスパース）

# キーワード

  * `inpos=1:p` 正のカウントのモデルに含まれる共変量列のインデックス
  * `inzero=1:p` ゼロカウントのモデルに含まれる共変量列のインデックス
  * `intercept::Bool=false` 各ハードル回帰にインターセプトを含める
  * `parallel::Bool=true` ポアソンフィットを並列化する
  * `local_cluster::Bool=true` 単一のマルチコアマシンに適したメモリを共有するローカルクラスター モード、または、メモリの共有がコストのかかるマシン間での分散により適したリモートクラスター モードを使用します。
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `select::SegSelect=MinAICc()` パスセグメント選択基準
  * `kwargs...` fit(Hurdle,...) に渡される追加のキーワード引数

```
