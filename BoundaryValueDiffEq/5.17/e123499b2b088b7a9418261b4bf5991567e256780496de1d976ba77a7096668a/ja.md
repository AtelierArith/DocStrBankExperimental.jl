```
BVPM2(; max_num_subintervals = 3000, method_choice = 4, diagnostic_output = 1,
    error_control = 1, singular_term = nothing)
BVPM2(max_num_subintervals::Int, method_choice::Int, diagnostic_output::Int,
    error_control::Int, singular_term)
```

2点境界値問題を解くためのFortranコード。詳細なドキュメントについては、[ODEInterface.jl](https://github.com/luchr/ODEInterface.jl/blob/master/doc/SolverOptions.md#bvpm2)を参照してください。

## キーワード引数:

```
- `max_num_subintervals`: 最大サブインターバルの数、デフォルトは3000。
- `method_choice`: IVPソルバーの選択、デフォルトは4次のルンゲ・クッタ法、
  利用可能な選択肢:
    - `2`: 2次のルンゲ・クッタ法。
    - `4`: 4次のルンゲ・クッタ法。
    - `6`: 6次のルンゲ・クッタ法。
- `diagnostic_output`: BVPM2の診断出力、デフォルトは非表示、利用可能な
  選択肢:
    - `-1`: 完全な診断出力。
    - `0`: 選択された出力。
    - `1`: 出力なし。
- `error_control`: RTOLが使用される誤差推定を決定し、デフォルトは
  欠陥制御、利用可能な選択肢:
    - `1`: 欠陥制御。
    - `2`: グローバル誤差制御。
    - `3`: 欠陥制御とその後のグローバル誤差制御。
    - `4`: 欠陥とグローバル誤差制御の線形結合。
- `singular_term`: ODEが左境界で特異項を持たない場合は何も指定せず、
  特異項のための定数(d,d)行列を指定します。
```

!!! 注     `ODEInterface`パッケージがロードされている場合のみ利用可能です。
