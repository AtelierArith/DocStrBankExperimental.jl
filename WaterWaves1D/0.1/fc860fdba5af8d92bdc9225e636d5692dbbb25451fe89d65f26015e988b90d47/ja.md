```
SolitarySGN(param; x₀=0)
```

`SolitaryWaveSerreGreenNaghdi(param; x₀=0)`に関連する初期データを構築します。これは、初期値問題`Problem(model, initial::InitialData, param)`で使用される`InitialData`型です。

---

```
SolitarySGN(c; ϵ=1,μ=1,x₀=0,N=2^12)
```

速度`c`、中心`x₀`、無次元パラメータ`ϵ`と`μ`、およびコレクションポイントの数`N`を持つ初期データを構築します。
