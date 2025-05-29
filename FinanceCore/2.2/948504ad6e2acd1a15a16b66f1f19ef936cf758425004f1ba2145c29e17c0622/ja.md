```
internal_rate_of_return(cashflows::vector)::Rate
internal_rate_of_return(cashflows::Vector, timepoints::Vector)::Rate
```

与えられた時間点で内部*利率*を計算します。時間点が指定されていない場合、最初のキャッシュフローが時間ゼロで発生し、その後の要素が時間1、2、3、...、nであると仮定して、等間隔のキャッシュフローの系列を仮定します。

期間ごとに1回の定期的な複利でRate型を返します（例えば、`timepoints`が年を表す場合は年次効果）。結果に対して`Yields.rate()`を呼び出すことでスカラー利率を取得します。

# 例

```julia-repl
julia> internal_rate_of_return([-100,110],[0,1]) # 例: 時間0と1でのキャッシュフロー
0.10000000001652906
julia> internal_rate_of_return([-100,110]) # 上記と同じことを暗示
0.10000000001652906
```

# ソルバーの注意事項

範囲[-2,2]内の根を返そうとします。高速ソルバーがこの条件に一致するものを見つけられない場合、より堅牢な検索が[.99,2]の範囲で実行されます。

返される解は範囲[-2,2]内にありますが、ゼロに最も近いものではない可能性があります。やや遅いですが、より堅牢なバージョンを使用するには、`ActuaryUtilities.irr_robust(cashflows,timepoints)`を直接呼び出してください。 ```
