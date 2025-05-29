```
function image_pass!(jump_model::JuMP.Model, input::Array{Float32, 4})
```

JuMPモデルを通じて画像をフォワードパスします。これは畳み込みニューラルネットワークを表しています。

ネットワークの出力、すなわち最後の全結合層ニューロンの活性化のベクトルを返します。
