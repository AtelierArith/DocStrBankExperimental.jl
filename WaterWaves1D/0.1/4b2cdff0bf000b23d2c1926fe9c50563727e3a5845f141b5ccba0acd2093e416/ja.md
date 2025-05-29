```
RK4(arguments;realdata)
```

明示的ルンゲ-クッタ第四次法ソルバー。

`Problem(model, initial, param; solver::TimeSolver)`で使用する`TimeSolver`型のオブジェクトを構築します。

引数は次のいずれかです。

0. 通常、ソルバーで解くモデルである`AbstractModel`型のオブジェクト；
1. サイズが`(N,datasize)`の`Array`、ここで`N`はコレクションポイントの数、`datasize`は解かれる方程式の数；
2. `(param,datasize)`、ここで`param`はキー`N`を含む`NamedTuple`、`datasize`は整数（オプション、デフォルトは`datasize=2`）。

キーワード引数`realdata`はオプションで、事前に割り当てられたベクトルが実数値か複素数値かを決定します。デフォルトでは、モデルによって、または`0.`および`1.`の場合は配列の型によって決定され、`2.`の場合は複素数値になります。
