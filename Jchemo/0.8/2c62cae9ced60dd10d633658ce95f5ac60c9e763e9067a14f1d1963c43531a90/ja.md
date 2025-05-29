```
dkplskdeda(; kwargs...)
dkplskdeda(X, y; kwargs...)
dkplskdeda(X, y, weights::Weight; kwargs...)
```

DKPLS-KDEDA.

  * `X` : Xデータ (n, p)。
  * `y` : 単変量クラスメンバーシップ (n)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。1以上でなければなりません。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。可能な値は: `:krbf`, `:kpol`。それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `prior` : クラスメンバーシップのための事前確率のタイプ。可能な値は: `:prop` (比例)、`:unif` (一様)、または各クラスの事前重みを与えるベクトル (ベクトルの場合、`mlev(y)` と同じ順序でソートされている必要があります)。
  * 関数 `dmkern` のキーワード引数 (バンド幅定義) もここで指定できます。
  * `scal` : ブール値。`true` の場合、PLS計算において `X` と Yダミーの各列はその未修正標準偏差でスケーリングされます。

関数 `plskdeda` (PLS-KDEDA) と同じですが、Yダミーテーブルに対してPLSR (関数 `plskern`) の代わりに直接カーネルPLSR (関数 `dkplsr`) が実行されます。

例については関数 `dkplslda` を参照してください。
