```
VanDerCorputSample(base::Integer, R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

van der Corput列は、根本的逆数列とも呼ばれ、単位区間を再帰的に同じサイズの部分に分割し、各区間に1つのサンプルを挿入する1次元の低偏差列です。

例えば、基数2の場合、この列は最初のパスで単位区間の各半分に1つの点を挿入することから始まります（最初の2つのサンプル）。次に、各四分の一、次に各八分の一、そしてそのように続きます。これにより、サンプルの数が基数の累乗の倍数である限り、よく層化されたサンプルが作成されます。
