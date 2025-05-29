```
ContWave{Boundary,T}
```

パッケージで実装されているさまざまなタイプのウェーブレットを包含する抽象型です。この抽象型は、要素出力タイプを与えるパラメータ `Boundary<:WaveletBoundary` と `T<:Number` を持っています。それぞれにはコンストラクタとデフォルトの事前定義されたエントリがあります。これらは次のとおりです：

  * `Morlet`: 平均が引かれた周波数領域のガウス関数である、複素的におおよそ解析的なウェーブレットです。`Morlet(σ::T) where T<: Real`。`σ` は母ウェーブレットの周波数領域の分散を与えます。`σ` がゼロに近づくと、すべての情報が空間的になります。デフォルトは `morl` で、$\sigma=2\pi$ です。

    $$
    \psi\hat(\omega) \propto \textrm{e}^{-\frac{\sigma^2}{2}}\big(\textrm{e}^{-(\sigma - \omega)^2} -\textrm{e}^{\frac{\omega^2-\sigma^2}{2}}\big)
    $$
  * `Paul{N}`: 複素的な解析ウェーブレットで、コーシーウェーブレットとも呼ばれます。`pauln` は `1:20` の n に対して、例えば `paul5` です。

    $$
    \psi\hat(\omega) \propto \chi_{\omega \geq 0} \omega^N\textrm{e}^{-\omega}
    $$
  * `Dog{N}`: ガウスの導関数で、N は導関数の数です。`dogn` は `0:6` の `n` に対して、Sombrero/メキシカンハット/マールウェーブレットは `n=2` です。

    $$
    \psi\hat(\omega) \propto \omega^N\textrm{e}^{-\frac{\omega^2}{2}}
    $$
  * `ContOrtho{OWT}`。OWT は [Wavelets.jl](https://github.com/JuliaDSP/Wavelets.jl) からの `OrthoWaveletClass` タイプのいくつかの直交ウェーブレットです。これは、これらの直交ウェーブレットのための母ウェーブレットの明示的な構成を使用して連続変換を行います。`ContOrtho(o::W)` を介して構築され、ここで `o` は Wavelets.jl からのものです。あるいは、次のように `ContOrtho` オブジェクトとして直接取得することもできます：

      * `cHaar` ハールウェーブレット
      * `cBeyl` ベイリキンウェーブレット
      * `cVaid` ヴァイディヤナタンウェーブレット
      * `cDbn` ダブシェーズウェーブレット。n は `1:Inf` の範囲です
      * `cCoifn` コイフレット。n は `2:2:8` の範囲です
      * `cSymn` シムレット。n は `4:10` の範囲です
      * `cBattn` バトル-ルマリエウェーブレット。n は `2:2:6` の範囲です
