```
expfit(n, seq, x, y; kwargs...)
```

データ `x` と `y` に n 指数関数をフィットさせます。

出力は `expfit_struct` 構造体です。

引数:

  * `n` : 指数項の数を指定する整数。
  * `seq` : パルスシーケンス。
  * `x` : 取得 x パラメータ（弛緩時間または拡散の b 因子）。
  * `y` : 取得 y パラメータ（磁化）。

オプションの引数:

  * `solver` : 最適化ソルバー、デフォルトは IPNewton()。
  * `normalize` : フィッティング前にデータを正規化しますか？（デフォルトは true）。
  * `L` : 最小化したい残差のノルムを指定する整数（デフォルトは 2）。

`n` 引数は初期パラメータの推定値のベクトルでもあり、その場合は使用される指数項の数も決定します。形式は [a1, b1, a2, b2, ...] で、a は振幅、b は指数関数内のパラメータです。

この場合、ベクトルの長さは偶数でなければなりません。

以下の例が明確にするのに役立つかもしれません:

`expfit([a,b] , CPMG, x, y)` -> 初期推定値 a * exp.( (1/b) * x) の単一指数フィット

`expfit([a,b,c,d] , CPMG, x, y)` -> 初期推定値 a * exp.( (1/b) * x) + c * exp.((1/d) * x) の二重指数フィット

`expfit([a,b,c,d,e,f] , CPMG, x, y)` -> 初期推定値 a * exp.( (1/b) * x) + c * exp.((1/d) * x) + e * exp.((1/f) * x) の三重指数フィット

（ここで a,b,c,d,e,f はあなたの選択した数です）

三重指数を超えるパラメータの数も使用できますが、推奨されません。
