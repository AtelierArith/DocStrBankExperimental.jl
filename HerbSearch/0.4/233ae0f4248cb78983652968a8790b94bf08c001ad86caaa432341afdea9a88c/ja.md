```
MHSearchIterator(examples::AbstractArray{<:IOExample}, cost_function::Function, evaluation_function::Function=HerbInterpret.execute_on_input)
```

`MHSearchIterator`は、メトロポリス・ヘイスティングスアルゴリズムを使用してプログラムを生成します。検索の挙動には以下の特徴があります：

  * `propose`関数には`random_fill_propose`を使用します。
  * `accept`関数は`確率的`です。
  * アルゴリズムの`温度`は時間とともに一定で、安定した受け入れ確率を保証します。

# 引数

  * `examples::AbstractArray{<:IOExample}`: 検索を導くために使用される入力-出力の例の配列。
  * `cost_function::Function`: 提案されたプログラムのコストを評価するための関数。
  * `evaluation_function::Function=HerbInterpret.execute_on_input`: 生成されたプログラムを評価し、出力を生成する関数。デフォルトは`HerbInterpret.execute_on_input`です。

# 戻り値

メトロポリス・ヘイスティングスアルゴリズムに従ってプログラムを生成するイテレータ。
