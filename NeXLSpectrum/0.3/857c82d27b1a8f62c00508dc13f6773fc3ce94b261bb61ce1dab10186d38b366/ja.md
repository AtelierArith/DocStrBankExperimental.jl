```
integrate(spec::Spectrum, channels::AbstractUnitRange{<:Integer})
integrate(spec::Spectrum, energyRange::StepRangeLen{Float64})
```

指定されたチャネルのすべてのカウントを合計します。バックグラウンド補正はありません。`energyRange` バージョンは、エネルギーがチャネルに完全にマッピングされない場合に部分チャネルからの分数寄与を含みます。

```
integrate(spec::Spectrum, back1::AbstractUnitRange{<:Integer}, peak::AbstractUnitRange{<:Integer}, back2::AbstractUnitRange{<:Integer})::UncertainValue
integrate(spec::Spectrum, back1::StepRangeLen{Float64}, peak::StepRangeLen{Float64}, back2::StepRangeLen{Float64})::UncertainValue
```

バックグラウンド区間を使用して、指定されたチャネルのすべてのカウントをバックグラウンド補正付きで合計します。

```
integrate(spec::Spectrum)
```

LLDからビームエネルギーまでのすべてのカウントの合計積分。
