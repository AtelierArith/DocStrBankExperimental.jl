```
CalculusWithJulia
```

Juliaを使用して微積分のトピックに関するノートを伴うパッケージです。[https://calculuswithjulia.github.io](https://calculuswithjulia.github.io)

このパッケージは2つのことを行います：

  * 他のいくつかのパッケージをロードし、それらが提供する機能を使いやすく（およびインストールしやすく）します。
  * 便利な関数をいくつか定義します。エクスポートされるものは

`unzip`、`rangeclamp`、`tangent`、`secant`、`D`（およびプライム記法）、`divergence`、`gradient`、`curl`、および`∇`、いくつかのプロット関数とともに。定数`e`は`exp(1)`に割り当てられています。

## `CalculusWithJulia`によってロードされるパッケージ

  * `SpecialFunctions`がロードされ、これらのノートで使用されるいくつかの特殊関数（例：`airyai`、`gamma`）にアクセスできます。
  * `ForwardDiff`パッケージがロードされ、自動微分を行うための`derivative`、`gradient`、`jacobian`、および`hessian`関数にアクセスできます。さらに、このパッケージは、関数の微分を返すために`'`（関数用）を定義し（[タイプの略奪](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Avoid-type-piracy-1)を犯します）、勾配を求めるための`∇`（`∇(f)`）、発散（`∇⋅F`）、および回転（`∇×F`）を求めるための`divergence`および`curl`を提供します。
  * `LinearAlgebra`パッケージがロードされ、ベクトル操作のためのいくつかの関数（`norm`、`cdot`（`⋅`）、`cross`（`×`）、`det`）にアクセスできます。
  * `PlotUtils`パッケージがロードされ、その`adapted_grid`関数が利用可能になります。

## ロード時に追加機能が追加されるパッケージ

拡張機能を通じて、または`Julia`パッケージ`Requires`を通じて、以下のパッケージがロードされるときに追加のコードが実行されます：

  * `SymPy`：記号数学用。
  * `Plots`：`Plots`パッケージはプロットインターフェースを提供します。

いくつかのプロットレシピが提供され、ノート内でのプロット作成を容易にします。`plotif`、`trimplot`、および`signchart`は単変数関数のプロットに使用され、`plot_polar`および`plot_parametric`は2次元または3次元の曲線をプロットするために使用されます。`plot_parametric`はパラメトリックに定義された表面のプロットを容易にします。`vectorfieldplot`および`vectorfieldplot3d`はベクトル場をプロットするために使用され、`arrow`は3Dベクトルを示す`quiver`への簡略化されたインターフェースです。

`plot_implicit`関数は`2D`の暗黙的プロットをプロットできます。（これは[ImplicitPlots.jl](https://github.com/saschatimme/ImplicitPlots.jl)から借用されており、他のパッケージを妨げる依存関係があるため避けられています。）

## 付随するノートで繰り返し登場する他のパッケージ：

  * `Roots`は単変数関数のゼロを見つけるために使用されます。
  * `SymPy`は記号数学用。
  * `QuadGK`および`HCubature`は数値積分に使用されます。
