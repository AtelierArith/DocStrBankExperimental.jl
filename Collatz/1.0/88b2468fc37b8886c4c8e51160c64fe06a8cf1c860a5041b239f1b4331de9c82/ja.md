```
hailstone_sequence(initial_value; P=2, a=3, b=1, max_total_stopping_time=1000, total_stopping_time=true, verbose=true)
```

コラッツ風の関数を反復することによって得られる連続する値のリストを返します。

1に到達するか、反復の総数がmax*total*stopping*timeを超えるまで続きます。total*stopping_timeがFalseの場合は、"stopping time"の値、すなわち初期値より小さい最初の値でハイルストーンが終了します。シーケンスはサイクルに遭遇したことを判断する能力を持っていますが、"1"からのサイクルは、デフォルトまたはカスタムのパラメータ設定に関係なく、サイクルの一部として試みられたり報告されたりすることはありません。"1"は"total stop"と見なされるためです。

# 引数

  * `initial_value::Integer`: ハイルストーンシーケンスを開始する値。

# キーワード引数

  * `P::Integer=2`: nを割るために使用されるモジュラス、nが(0 mod P)に等しい場合。
  * `a::Integer=3`: nを掛けるための係数。
  * `b::Integer=1`: nのスケーリングされた値に加える値。
  * `max_total_stopping_time::Integer=1000`: 1に到達しない場合の関数を反復する最大回数。
  * `total_stopping_time::Bool=true`: "total"ストッピングタイム（1を得るための反復回数）まで実行するか、通常のストッピングタイム（初期値より小さい値に到達するための反復回数）まで実行するか。
  * `verbose::Bool=true`: 詳細モードに設定されている場合、ハイルストーンシーケンスは、ストッピングタイムに到達したかサイクルに入ったかに関する情報を提供する制御文字列シーケンスを含みます。

# 例

```jldoctest
julia> print(hailstone_sequence(16, verbose=false))
[16, 8, 4, 2, 1]
```

```jldoctest
julia> print(hailstone_sequence(16))
Any[16, 8, 4, 2, 1, Any[Collatz._CC.TOTAL_STOPPING_TIME, 4]]
```

```jldoctest
julia> print(hailstone_sequence(761, P=5, a=2, b=3, verbose=false))
[761, 1525, 305, 61, 125, 25, 5, 1]
```

# サイクルの例！

```jldoctest
julia> print(hailstone_sequence(-56))
Any[-56, -28, Collatz._CC.CYCLE_INIT, Any[-14, -7, -20, -10, -5], Any[Collatz._CC.CYCLE_LENGTH, 5]]
```

```jldoctest
julia> print(hailstone_sequence(-56, verbose=false))
[-56, -28, -14, -7, -20, -10, -5, -14]
```
