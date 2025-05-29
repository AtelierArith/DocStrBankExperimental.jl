```
SolitaryWGN(param; kwargs)
```

`SolitaryWaveWhithamGreenNaghdi(param; kwargs)`に関連付けられた初期データを構築し、初期値問題`Problem(model, initial::InitialData, param)`で使用します。

---

```
SolitaryWGN(c; ϵ=1,μ=1,N=2^12,kwargs)
```

速度`c`、無次元パラメータ`ϵ`と`μ`、およびコレクションポイントの数`N`を持つ初期データを構築し、`kwargs`は上記の他の（オプションの）キーワード引数です。
