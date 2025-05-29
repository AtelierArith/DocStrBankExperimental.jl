```
Options(;
    radius = .1, 
    bounds, 
    n_iters, 
    init_parms,
    parallel = false,
    adapt_radius! = adapt!,
    kwargs...
)
```

MCMCサンプラーの設定オプションを保持するオブジェクトです。

# フィールド

  * `parallel=false`: trueの場合、スレッドでモデルを実行します。関数の評価時間が1ms以上の場合、速度向上が観察されます。
  * `radius = .10`: 各チェーンの初期半径の長さ
  * `bounds`: パラメータ空間の各次元に対する（下限、上限）を表すタプルのベクター
  * `x_range`: 各パラメータの許容値の範囲
  * `n_iters`: 実行する反復の数
  * `p_eval`: モデルとパターン関数を評価する関数
  * `adapt_radius!=adapt!`: 半径を適応させる`func(chain, options; kwargs...)`の形式の関数。
  * `init_parms`: 2次元の場合のように[[.3,.4],[.3,.5]]などの開始点のベクター。
  * `n_dims`: パラメータ空間の次元数
  * `parm_names`: パラメータ名に対応するシンボルのベクター。デフォルトは[:p1,:p2,..:pn]
  * `add_iters`: 同じ領域にある同じパターンを持つチェーンをマージした後に実行する試行の数
