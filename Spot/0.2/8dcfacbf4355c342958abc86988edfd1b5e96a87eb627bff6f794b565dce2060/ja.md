```
LTLTranslator
```

線形時間論理式をオートマトンに変換します

# フィールド

  * tgba::Bool = true  遷移ベースの一般化ブッヒオートマトンを出力します
  * buchi::Bool = false 状態ベースのブッヒオートマトンを出力します
  * monitor::Bool = false モニターを出力します
  * deterministic::Bool = true 一般的なものと組み合わせると、決定論的オートマトンを生成するために必要なことを行い、任意の受理条件を使用することがあります
  * generic::Bool = true
  * parity::Bool = true 決定論的と組み合わせると、パリティ受理を持つ決定論的オートマトンを生成します
  * state*based*acceptance::Bool = true 状態を使用して受理を定義します
