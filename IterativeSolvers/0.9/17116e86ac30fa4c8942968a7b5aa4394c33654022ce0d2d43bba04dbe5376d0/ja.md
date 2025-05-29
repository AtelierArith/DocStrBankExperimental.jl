一般的かつ詳細な情報を反復法について保存します。

# フィールド

`mvps::Int`: 行列ベクトル積の数。

`mtvps::Int`: 転置行列ベクトル積の数。

`iters::Int`: メソッドによって行われた反復回数。

`restart::T`: 再起動に関連する情報。

  * `T == Int`: 再起動ごとの反復回数。
  * `T == Nothing`: 再起動のないメソッド。

`isconverged::Bool`: メソッドの収束。

`data::Dict{Symbol,Any}`: メソッド実行中に保存されたすべての情報を保存します。許容誤差、残差、その他の情報（例: [`svdl`](@ref) のリッツ値）を保存します。

# コンストラクタ

```
ConvergenceHistory()
ConvergenceHistory(restart)
```

空のフィールドを持つ `ConvergenceHistory` を作成します。

# 引数

`restart`: 再起動ごとの反復回数。

# プロット

`Plots.jl` パッケージを使用したプロットをサポートします。ベクトルは系列として、行列は散布図としてプロットされます。

# 実装

`Base`: `getindex`, `setindex!`, `push!`
