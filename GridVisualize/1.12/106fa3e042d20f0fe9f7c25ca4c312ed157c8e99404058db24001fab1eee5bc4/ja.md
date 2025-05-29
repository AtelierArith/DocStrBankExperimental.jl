```
GridVisualize
```

[![Build status](https://github.com/WIAS-PDELib/GridVisualize.jl/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/WIAS-PDELib/GridVisualize.jl/actions/workflows/ci.yml?query=branch%3Amain) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://WIAS-PDELib.github.io/GridVisualize.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://WIAS-PDELib.github.io/GridVisualize.jl/dev) [![code style: runic](https://img.shields.io/badge/code_style-%E1%9A%B1%E1%9A%A2%E1%9A%BE%E1%9B%81%E1%9A%B2-black)](https://github.com/fredrikekre/Runic.jl)

# GridVisualize

[ExtendableGrids.jl](https://github.com/WIAS-PDELib/ExtendableGrids.jl) のプロット用コンパニオンモジュール。1次元、2次元、または3次元の空間次元における単純なグリッド上で、グリッド、スカラーの区分線形関数、およびベクトル（2Dのみ）のプロットを提供します。主にサポートされているバックエンドはCairoMakie、GLMakie、PyPlot、およびPlutoVistaです。Plotsは部分的にサポートされています（1Dおよび2Dの長方形グリッド）。

## 免責事項

コードはかなり複雑で、多くのコードパスはテストが難しいです。問題を修正するための支援をする準備をしてください。

## サンプル使用法：

### グリッド、関数、またはベクトルフィールドのプロット

```
gridplot(grid, Plotter=GLMakie)
scalarplot(grid, function,Plotter=GLMakie)
vectorplot(grid, vectorfunction,Plotter=GLMakie)
streamplot(grid, vectorfunction,Plotter=GLMakie)
```

これは1/2/3Dグリッドに対して機能し、グリッドのノード上の値で表される関数、またはそれぞれ1、2、または3変数のスカラー関数を使用します。ベクトルおよびストリームプロットは現在2Dのみに利用可能です。

`grid`引数は、[ExtendableGrids.jl](https://github.com/WIAS-PDELib/ExtendableGrids.jl)パッケージによって定義された`ExtendableGrid`である必要があります。`grid`の代わりに、グリッドを記述するために次の引数を渡すことができます（これにより、内部的にオンザフライで作成されます）：

  * 1Dグリッドを指定する`AbstractVector` `X`
  * 2Dグリッドを指定する`AbstractVector`s `X,Y`
  * 3Dグリッドを指定する`AbstractVector`s `X,Y,Z`
  * `coord, cellnodes`、ここで`coord`は点の座標の`dim x nn`行列で、`cellnodes`は単純体ノードインデックスの`dim+1 x nc`接続行列であり、`nn`ノードと`nc`単純体を持つ`dim`次元の単純体グリッドを記述します。

プロットの外観は、[キーワード引数](https://WIAS-PDELib.github.io/GridVisualize.jl/dev/api/#GridVisualize.available_kwargs)によって調整できます。

### プロッター

プロッターは、例えばPlots、PyPlot、GLMakie、CairoMakie、PlutoVistaなどです - パッケージによってエクスポートされたモジュールを渡します。異なるプロッターを同時に使用できます。

### 1つのプロットウィンドウでの複数のプロット

```
vis=GridVisualizer(Plotter=GLMakie, layout=(1,2))
gridplot!(vis[1,1],grid)
scalarplot!(vis[1,2],grid,function)
reveal(vis)
```

### 一時的なプロット

これは、GLMakieのためのオブザーバブルを介した高速更新と、PlutoVistaのための永続的なdivを使用します。

```
vis=GridVisualizer(Plotter=GLMakie)
for i=1:N
   function=calculate(i)
   scalarplot!(vis,grid,function)
   reveal(vis)
end
```

### 映画

現在、これらはGLMakie、CairoMakie、およびPlotsバックエンドでREPLおよびPlutoノートブックの両方から記録できます。MP4ファイルとGIFを作成できます。PyPlotもおそらく続くでしょう。

これはREPLでアニメーショングラフィックを表示し（基本的に上記と同じ）、Plutoノートブックに埋め込まれたビデオを作成します：

```
vis=GridVisualizer(Plotter=Plots)
movie(vis) do vis
  for i=1:N
     function=calculate(i)
     scalarplot!(vis,grid,function)
     reveal(vis)
  end
end
```

ノートブックやREPLで表示するのではなく、ファイルに保存するには、次のようにします：

```
vis=GridVisualizer(Plotter=CairoMakie)
movie(vis, file="video.mp4") do vis
  for i=1:N
     function=calculate(i)
     scalarplot!(vis,grid,function)
     reveal(vis)
  end
end
```

### デフォルトプロッターの設定

`GridVisualizer`、`gridplot`、または`scalarplot`への呼び出しで`Plotter`を指定する代わりに、デフォルトプロッターを設定できます：

```
default_plotter!(PyPlot)
gridplot(grid)
scalarplot(grid, function)
```

または 

```
default_plotter!(GLMakie)
vis=GridVisualizer(layout=(1,2))
gridplot!(vis[1,1],grid)
scalarplot!(vis[1,2],grid,function)
```

### プロットをオフにする

それぞれの場所で`Plotter=nothing`を渡すか、`default_plotter!(nothing)`を設定すると、すべてのプロット関数は何もしなくなります。

## 利用可能なプロットバックエンドと機能。

  * 'y': 利用可能
  * 'i': ある程度のインタラクティブな制御
  * '(y)': 長方形グリッドでのみ利用可能
  * 'p': 計画中（ただしスケジュールはありません）
  * 'n': おそらく将来的にも無理

|                | PyPlot | Makie | PlutoVista | Plots | VTKView |
| --------------:| ------:| -----:| ----------:| -----:| -------:|
| scalarplot, 1D |      y |     y |        y,i |     y |       y |
| vectorplot, 1D |      y |     y |          y |     y |       y |
|   gridplot, 1D |      y |     y |          y |     y |         |
| scalarplot, 2D |      y |     y |          y |   (y) |     y,i |
| vectorplot, 2D |      y |     y |          y |     y |         |
| streamplot, 2D |      y |     y |          p |     n |         |
|   gridplot, 2D |      y |   y,i |          y |   (y) |     y,i |
| scalarplot, 3D |      y |   y,i |        y,i |     n |     y,i |
|   gridplot, 3D |      y |   y,i |        y,i |     n |     y,i |
| vectorplot, 3D |      p |     p |          p |     n |         |
| streamplot, 3D |        |     p |          p |     n |         |
|          movie |      n |     y |          n |     y |         |

## サンプル出力

### [PyPlot](https://github.com/JuliaPy/PyPlot.jl):

![](https://github.com/WIAS-PDELib/GridVisualize.jl/blob/main/docs/src/assets/multiscene_pyplot.png?raw=true)

### [GLMakie](https://github.com/JuliaPlots/GLMakie.jl):

![](https://github.com/WIAS-PDELib/GridVisualize.jl/blob/main/docs/src/assets/multiscene_glmakie.png?raw=true)

### [Plots/gr](https://github.com/JuliaPlots/Plots.jl):

![](https://github.com/WIAS-PDELib/GridVisualize.jl/blob/main/docs/src/assets/multiscene_plots.png?raw=true")

### [VTKView](https://github.com/j-fu/VTKView.jl):

![](https://github.com/WIAS-PDELib/GridVisualize.jl/blob/main/docs/src/assets/multiscene_vtkview.png?raw=true")

## vscode

Visual Studio Codeのプロットペインへのプロットが機能しています。ここでは、CairoMakieまたはWGLMakieをバックエンドとして使用できます。これは、変異関数のみで機能します。つまり、次のようにする必要があります。

```
vis=GridVisualizer(Plotter=WGLMakie)
gridplot!(vis,grid,clear=true,show=true)
```

## ノートブック

### Pluto

CairoMakie、PyPlot、Plots、GLMakieのPlutoノートブックでのプロットが機能しており、WGLMakieはおそらくJSServeとの組み合わせで機能します。

Plutoノートブックでのプロットは、[plotly.js](https://plotly.com/javascript/)（1D）および[vtk.js](https://kitware.github.io/vtk-js/index.html)（2/3D）に基づく[PlutoVista.jl](https://github.com/j-fu/PlutoVista.jl)を使用できます。例のノートブックを参照してください：[pluto](https://raw.githubusercontent.com/WIAS-PDELib/GridVisualize.jl/main/examples/plutovista.jl)、[html](https://WIAS-PDELib.github.io/GridVisualize.jl/dev/plutovista.html)。

### Jupyter

Jupyterでも機能する可能性があります。テストや修正にボランティアしたい場合は、私に連絡してください。
