```
fit_mle(mix::AbstractArray{<:MixtureModel}, y::AbstractVecOrMat, weights...; method = ClassicEM(), display=:none, maxiter=1000, atol=1e-3, rtol=nothing, robust=false, infos=false)
```

`fit_mle`と同様に、mix配列内の各（初期）混合物に対して実行します。その後、最も大きな対数尤度を持つものを選択します。警告：EMが特異な解に収束する場合のエラーメッセージを回避するためにtryとcatchを使用します（おそらく、robustを使用することでほとんどのケースでエラーを回避できるはずです）。
