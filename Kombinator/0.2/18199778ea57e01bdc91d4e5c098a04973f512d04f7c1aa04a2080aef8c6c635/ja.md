```
struct LagrangianAlgorithm <: CombinatorialAlgorithm
```

インスタンスを解決するためにラグランジュ緩和を使用し、その後に洗練ステップを行います。これは、他のアルゴリズムに基づいて新しい制約を持つ問題のアルゴリズムを構築するのに特に便利です。これらの手法は、ラグランジュ緩和に基づいて定数加法近似をもたらすことがよくあります。
