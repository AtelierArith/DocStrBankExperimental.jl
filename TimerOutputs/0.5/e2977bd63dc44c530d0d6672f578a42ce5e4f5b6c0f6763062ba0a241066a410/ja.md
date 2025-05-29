```
begin_timed_section!([to::TimerOutput=DEFAULT_TIMER], label::String)
```

指定されたラベルでセクションのタイミングを開始します。セクションが終了したときに `end_timed_section!` に渡すべき `SectionTimeData` オブジェクトを返します。
