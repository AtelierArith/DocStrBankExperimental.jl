```
RobustMADS(N; search = NoSearch(), poll = LTDirectionGenerator(N),
              mesh = LogMesh(), kernel = GaussKernel(1, 1), cache = Cache(N))
```

`N`が問題の次元である`RobustMADS`オブジェクトを返します。Audet et al. 2018を参照してください。
