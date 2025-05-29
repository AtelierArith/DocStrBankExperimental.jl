```
ELM(n_hidden_neurons::Int,input_data::AbstractArray{T},output_data::AbstractArray{T}; activation::Function = sigmoid, regularization::T = zero(T)) where T<:AbstractFloat
```

隠れニューロンの数、入力、および出力を渡してELMを構築します。キーワード引数として、異なる活性化関数（デフォルト = sigmoid）を渡すこともできます。入力は以下の形式である必要があります。 | 特徴1| 特徴2| |––––-|––––-| |  エントリ1 |  エントリ1 | |  エントリ2 |  エントリ2 |
