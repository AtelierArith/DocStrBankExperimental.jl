```
body_forces(surfaces, properties, reference, freestream, symmetric; kwargs...)
```

パネルのプロパティに基づいてボディフォース係数を返します。

この関数は、パネルフォースを取得するために近接場解析がすでに実行されていることを前提としています。

# 引数:

  * `surfaces`: 各サーフェスがサーフェスパネルの行列（[`SurfacePanel`](@ref）を参照）で表されるサーフェスのコレクション。形状は (nc, ns) で、`nc` は弦方向のパネルの数、`ns` はスパン方向のパネルの数です。
  * `properties`: 各サーフェスのサーフェスプロパティ。各サーフェスのサーフェスプロパティは、パネルプロパティの行列（[`PanelProperties`](@ref）を参照）で表され、形状は (nc, ns) で、`nc` は弦方向のパネルの数、`ns` はスパン方向のパネルの数です。
  * `reference`: 参照パラメータ（[`Reference`](@ref）を参照）
  * `freestream`: フリーストリームパラメータ（[`Freestream`](@ref）を参照）
  * `symmetric`: （必須）各サーフェスに対して、誘導速度を計算する際にミラーイメージ（X-Z平面に対して）が使用されたかどうかを示すフラグ
  * `frame`: `CF` と `CM` を返すフレーム。オプションは [`Body()`](@ref)（デフォルト）、[`Stability()`](@ref）、および [`Wind()`](@ref) です。
