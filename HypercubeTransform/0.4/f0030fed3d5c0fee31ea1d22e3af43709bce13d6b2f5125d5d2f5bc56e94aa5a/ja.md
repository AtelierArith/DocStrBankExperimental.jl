```
asflat(d::Distribution)
```

分布 `d` のサポートの変換を計算し、変数が ℝⁿ 上に存在するようにします。ここで n は問題の次元です。これは、モデルの再パラメータ化を行う際に Turing と Stan が実際に行うことです。

返されるオブジェクトは `TransformVariables.AbstractTransform` オブジェクトであり、そのインターフェースに従います。詳細については、[TransformVariable docs](https://www.tamaspapp.eu/TransformVariables.jl/stable/) を参照してください。
