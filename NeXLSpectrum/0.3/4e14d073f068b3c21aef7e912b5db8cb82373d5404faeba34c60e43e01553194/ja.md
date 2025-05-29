```
FilterFitResult
```

FilteredUnknownWをFilteredUnknownにフィッティングした結果を表します。

構造体要素

```
label::UnknownLabel  # 不明を識別します
kratios::UncertainValues # ReferenceLabelオブジェクトでラベル付けされた値
roi::UnitRange{Int} # フィットされたチャネルの範囲
raw::Vector{T} # 生のスペクトルデータ
residual::Deferred # 残差スペクトル
peakback::Deferred # {Dict{ReferenceLabel,NTuple{3,Float64}}} ピークカウント、バックグラウンドカウント、およびカウント/(nAs)を含みます
```

asa(DataFrame, ffr::FilterFitResult)を使用して、表形式で要約します。
