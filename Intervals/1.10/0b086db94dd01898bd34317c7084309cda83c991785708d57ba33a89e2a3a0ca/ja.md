```
AnchoredInterval{P,T,L,R}
```

`AnchoredInterval`は、2つの端点ではなく、単一の`anchor`ポイントと範囲のサイズを表す値の型`P`によって定義される非反復可能な範囲またはスパンのサブタイプである`AbstractInterval`です。`P`が正のとき、`anchor`は小さい端点（範囲の始まり）を表し、`P`が負のとき、`anchor`は大きい端点（範囲の終わり）を表します。

`AnchoredInterval`値によって表される区間は、閉じた（両端点が区間に含まれる）、開いた（どちらの端点も含まれない）、または半開きのいずれかです。この開放性は、`L`と`R`の境界タイプによって定義され、`P`の正の値に対して小さい端点が含まれ、負の値に対して大きい端点が含まれる半開きがデフォルトです。

### なぜ？

`AnchoredIntervals`は、単一の値が値の範囲を代表する場合に最も便利です。これは、日付や時刻で最もよく発生し、「HE15」はしばしば（14:00..15:00]の短縮形として使用されます。

この目的のために、`HourEnding`は`AnchoredInterval{Hour(-1)}`の型エイリアスです。同様に、`HourBeginning`は`AnchoredInterval{Hour(1)}`の型エイリアスです。

### 丸め

ユーザーは`HourEnding`または`HourBeginning`値が特定の時間に固定されることを期待するかもしれませんが、コンストラクタは提供されたアンカーが丸められていることを保証しません：

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> HourEnding(DateTime(2016, 8, 11, 2, 30))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T02:30:00"))
```

`HE`および`HB`の擬似コンストラクタは、適切に入力を最寄りの時間に切り上げまたは切り下げます：

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> HE(DateTime(2016, 8, 11, 2, 30))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T03:00:00"))

julia> HB(DateTime(2016, 8, 11, 2, 30))
HourBeginning{DateTime, Closed, Open}(DateTime("2016-08-11T02:00:00"))
```

### 例

```jldoctest; setup = :(using Intervals, Dates), filter = r"AnchoredInterval\{(Day|Hour|Minute)\(-?\d+\),|Hour(Ending|Beginning)\{"
julia> AnchoredInterval{Hour(-1)}(DateTime(2016, 8, 11, 12))
HourEnding{DateTime, Open, Closed}(DateTime("2016-08-11T12:00:00"))

julia> AnchoredInterval{Day(1)}(DateTime(2016, 8, 11))
AnchoredInterval{Day(1), DateTime, Closed, Open}(DateTime("2016-08-11T00:00:00"))

julia> AnchoredInterval{Minute(5),Closed,Closed}(DateTime(2016, 8, 11, 12, 30))
AnchoredInterval{Minute(5), DateTime, Closed, Closed}(DateTime("2016-08-11T12:30:00"))
```

参照：[`Interval`](@ref)、[`HE`](@ref)、[`HB`](@ref)
