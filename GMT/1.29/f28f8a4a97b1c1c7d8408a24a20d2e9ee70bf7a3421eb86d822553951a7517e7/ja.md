```
marginalhist(data; kwargs...)
```

Mx2配列を取り、最初の列と2番目の列の散布図を作成します。デフォルトでは、ポイント数が<= 200の場合はscatter3プロットを行い、それ以外の場合はbihexプロットを行いますが、これは設定可能です。入力`data`はMxN行列、`GMTdataset`、または`gmtread`で読み込むと`GMTdataset`を返すファイル名であることができます。

  * `marginalhist(data)`: *x,y* 散布図をプロットし、*x* と *y* の周辺ヒストグラムを表示します。
  * `marginalhist(..., frac|fraction=xx)`: 図のサイズに対する周辺プロットの割合サイズを設定します。デフォルトは0.15（15%）です。
  * `marginalhist(..., hexbin=true)`: ポイント数が<= 2000の場合でもhexbinプロットを強制します。
  * `marginalhist(..., scatter=true)`: ポイント数が> 2000の場合でも散布図を強制します。
  * `marginalhist(..., density=true)`: サイドプロットにはヒストグラムの代わりにデータカーネル密度が含まれます。
  * `marginalhist(..., gap=xx)`: 図と周辺プロットの間の隙間をセンチメートル単位で設定します。
  * `marginalhist(..., histcolor|histfill=color)`: 選択した色でサイドヒストグラム/密度を塗ります（histcolor=:noneで塗らない）。
  * `marginalhist(..., nocbar=true)`: hexbinプロットを行う際にカラーバーをプロットしないようにします。
  * `marginalhist(..., histkw=args)`: `args`はヒストグラムプロットを制御するパラメータを持つNamedTupleです（`region`と`figsize`を除く、`histogram`モジュールに渡されるのと同じオプション）。

`kwargs`にはプロットの詳細を制御するために使用できるいくつかのオプションがあり（`subplot`、`binstats`、`plot`関数に渡されます）。

例:     marginalhist(randn(2500,2), scatter=true, histkw=(annot=true,), show=true)

```
marginalhist(randn(2000,2), histkw=(frame="none", fill=:green, W="0@100"), show=true)

marginalhist(randn(2500,2), cmap=:magma, density=true, show=1)
```
