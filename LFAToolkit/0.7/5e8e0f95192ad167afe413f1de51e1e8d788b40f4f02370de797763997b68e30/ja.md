```julia
BDDC(operator, injectiontype)
```

有限要素演算子のためのBDDC前処理器

# 引数:

  * `operator::Operator`:                前処理する有限要素演算子
  * `injectiontype::BDDCInjectionType`:  使用する部分組み立て空間への注入のタイプ

# 戻り値:

  * BDDC前処理器オブジェクト
