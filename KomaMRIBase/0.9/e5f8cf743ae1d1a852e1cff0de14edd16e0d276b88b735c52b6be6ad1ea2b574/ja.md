```
timecurve = TimeCurve(t, t_unit, periodic, periods)
```

TimeCurve構造体。これは、運動の時間的挙動を表す時間曲線を定義する特化型です。この曲線は、水平（x軸）および垂直（y軸）軸をそれぞれ表す2つのベクトル `t` と `t_unit` によって定義されます。ある程度、この曲線は、動画編集、3Dシーン作成、またはゲーム開発のソフトウェアで一般的に見られるアニメーション曲線に関連付けることができます。

さらに、TimeCurve構造体には、互いに独立した2つのフィールドが含まれています。`periodic` は、時間曲線が定期的に繰り返されるべきかどうかを示すブール値です。`periods` には、時間曲線で望まれる繰り返しの数だけ要素が含まれています。各要素は、その繰り返しのスケーリングファクターを指定します。

# 引数

  * `t`: (`::AbstractVector{<:Real}`, `[s]`) 時間ベクトル
  * `t_unit`: (`::AbstractVector{<:Real}`) yベクトル、0と1の間でスケーリングする必要があります
  * `periodic`: (`::Bool`, `=false`) 時間曲線が定期的に繰り返されるべきかどうかを示します
  * `periods`: (`::Union{<:Real,AbstractVector{<:Real}}`, `=1.0`): 各期間の相対的な持続時間を、`t[end] - t[1]` で定義された基準持続時間に対して表します。言い換えれば、特定の期間を長くしたり短くしたりするためのスケーリングファクターとして機能します。これにより、不整脈や他の周期性の変動などのパターンを作成することができます。

# 戻り値

  * `timecurve`: (`::TimeCurve`) TimeCurve構造体

# 例

1. 単一の繰り返しを持つ非周期的運動:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 0.2, 0.5, 1.0])
```

![Time Curve 1](../assets/time-curve-1.svg)

2. 単一の繰り返しを持つ周期的運動:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periodic=true)
```

![Time Curve 2](../assets/time-curve-2.svg)

3. 複数の繰り返しを持つ非周期的運動:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periods=[1.0, 0.5, 1.5])
```

![Time Curve 3](../assets/time-curve-3.svg)

4. 複数の繰り返しを持つ周期的運動:

```julia-repl
julia> timecurve = TimeCurve(t=[0.0, 0.2, 0.4, 0.6], t_unit=[0.0, 1.0, 1.0, 0.0], periods=[1.0, 0.5, 1.5], periodic=true)
```

![Time Curve 4](../assets/time-curve-4.svg)
