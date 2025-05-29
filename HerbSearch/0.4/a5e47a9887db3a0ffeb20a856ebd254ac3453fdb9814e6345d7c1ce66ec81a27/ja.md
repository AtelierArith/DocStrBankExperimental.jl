```
SASearchIterator(spec, cost_function, initial_temperature=1, temperature_decreasing_factor = 0.99, evaluation_function::Function=HerbInterpret.execute_on_input)
```

シミュレーテッドアニーリングサーチアルゴリズムに従って実行される列挙子を返します。

  * `spec` : 例の配列
  * `cost_function` : 提案されたプログラムを評価するコスト関数
  * `initial_temperature` : アルゴリズムの開始温度
  * `temperature_decreasing_factor` : 時間の温度の減少因子
  * `evaluation_function` : 生成されたプログラムを評価し、出力を生成する評価関数

提案関数は `random_fill_propose` です（メトロポリス・ヘイスティングスと同じ）。受け入れ関数は確率的ですが、温度も考慮に入れます。
