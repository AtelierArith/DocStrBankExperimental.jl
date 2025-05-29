```
CTMC{T<:AbstractFloat, U<:Int}
```

状態遷移の完全な軌跡を格納する連続時間マルコフ連鎖の表現。

# フィールド

  * `simulation_time::T`: 総シミュレーション時間
  * `transition_times::Vector{T}`: 状態が変化した時間点、0.0から始まる
  * `states::Vector{U}`: 各遷移時間で入った状態のシーケンス、初期状態から始まる

# 型パラメータ

  * `T`: 時間値の浮動小数点型
  * `U`: 状態インデックスの整数型

# 注

`states` と `transition_times` ベクターは同じ長さを持ち、`states[i]` の各エントリは `transition_times[i]` の時点で入った状態を表します。システムは `transition_times[i+1]` の時点まで `states[i]` に留まります。
