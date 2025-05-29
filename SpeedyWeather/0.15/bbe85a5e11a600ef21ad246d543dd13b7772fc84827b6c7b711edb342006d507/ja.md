コールバックのスケジュールは、指定された期間が経過した後（最初のタイムステップを除く）または特定の時間（初期時間を除く）に定期的に実行されるようにします。2つの連続したタイムステップ i, i+1 に対して、イベントは (i,i+1] の間に発生した場合に i+1 にスケジュールされます。同様に、周期 p の定期スケジュールは start+p で実行されますが、p はモデルのタイムステップの倍数に合わせて丸められます。定期スケジュールとイベントスケジュールは組み合わせることができ、両方で実行されます。スケジュールはコールバックにフィールドとして追加されることを意図しています。

```
Base.@kwdef struct MyCallback
    schedule::Schedule = Schedule(every=Day(1))
    other_fields
end
```

初期化に関しては、`initialize!(::Schedule,::Clock)` および `isscheduled(::Schedule,::Clock)` を参照してください。フィールド

  * `every::Dates.Second`: [OPTION] 各時間期間を実行、最初のタイムステップを除く。デフォルト=実行しない。
  * `times::Vector{Dates.DateTime}`: [OPTION] 時間にスケジュールされたイベント
  * `schedule::BitVector`: 実際のスケジュール、true=このタイムステップを実行、false=実行しない
  * `steps::Int64`: スケジュールされた実行の数
  * `counter::Int64`: 実行の数をカウントアップ
