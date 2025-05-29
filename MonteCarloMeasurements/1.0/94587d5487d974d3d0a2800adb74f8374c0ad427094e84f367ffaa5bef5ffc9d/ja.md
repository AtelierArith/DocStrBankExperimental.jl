```
struct StaticParticles{T, N} <: AbstractParticles{T, N}
```

`?Particles` を参照してヘルプを確認してください。`StaticParticles` と `Particles` の違いは、`StaticParticles` が粒子を静的ベクトルに格納することです。これにより、実行時間は短くなりますが、コンパイル時間は長くなります。いくつかのベンチマークについてはドキュメントを参照してください。サンプルサイズは ≲ 300-400 の場合にのみ推奨されます。
