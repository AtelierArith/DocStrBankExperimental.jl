```
bootstrap([rng::AbstractRNG,] p::Particles, n = nparticles(p))
```

置換えで再サンプリングされたParticlesを返します。`n`は引き出すサンプルの数を指定します。Particlesの配列にも対応しており、その場合は単一のインデックスセットが引き出され、配列内のすべての要素からサンプルを抽出するために使用されます。
