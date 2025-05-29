```
IrrationalPowerMultiple
```

改善された `Irrational`。非ゼロの [`TypeDomainInteger`](@ref) 指数と非ゼロの [`TypeDomainRational`](@ref) 因子を `Irrational` と一緒に格納することにより、[`TypeDomainRational`](@ref) および `Irrational` との正確な算術をサポートします。

コンストラクタは `Irrational` から変換します。

[`TypeDomainRational`](@ref)、[`TypeDomainNaturalLogarithm`](@ref) および `Irrational` との正確な算術をいくつかサポートします。

3つの型パラメータがあります：

  * 基数
  * 基数が上げられる指数
  * 残りが掛け合わされる因子

現在は抽象型であるにもかかわらず、このパッケージの外部から `IrrationalPowerMultiple` をサブタイプ化することは禁止されています。
