```
TetGen
```

# TetGen

[![linux-macos-windows](https://github.com/JuliaGeometry/TetGen.jl/actions/workflows/ci.yml/badge.svg)](https://github.com/JuliaGeometry/TetGen.jl/actions/workflows/ci.yml) [![Codecov](https://codecov.io/gh/JuliaGeometry/TetGen.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JuliaGeometry/TetGen.jl) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/JuliaGeometry/TetGen.jl/blob/master/LICENSE) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://JuliaGeometry.github.io/TetGen.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://JuliaGeometry.github.io/TetGen.jl/dev) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl)

`TetGen.jl`パッケージは、C++プロジェクト[TetGen](https://wias-berlin.de/software/index.jsp?id=TetGen&lang=1)のJuliaラッパーです。このラッパーは、TetGenに基づく四面体メッシングと（制約付き）3Dデローニーおよびボロノイタイルを可能にします。

TetGenが役立つと感じた場合は、Hang Siの論文「TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator」を引用してください。ACM Trans. on Mathematical Software. 41 (2), 2015 [http://doi.acm.org/10.1145/2629697](http://doi.acm.org/10.1145/2629697)。

## ライセンス

TetGen.jlをインストールすると、TetGenライブラリのコンパイル済みライブラリバージョンが[TetGen_jll.jl](https://github.com/JuliaBinaryWrappers/TetGen_jll.jl)リポジトリからダウンロードされます。このライブラリは[Affero Gnu Public License v3 (AGPL)](https://www.gnu.org/licenses/agpl-3.0.html)に従いますが、このパッケージのTetGen.jlにおけるライブラリへのバインディングはMITライセンスの下にあります。これは、TetGen.jlのバインディングを介してTetGenライブラリを使用するコードがTetGenのライセンス条件に従うことを意味します。カバーされた作品、すなわちTetGenライブラリにリンクし、TetGenライブラリと共に配布されるプログラムを配布する場合、その配布はAGPLv3の条件に従います。

他のオプションについては、[TetGenライセンスFAQ](http://wias-berlin.de/software/tetgen/1.5/FAQ-license.html)を参照してください。

## GeometryBasicsデータ型を使用した例

```julia
using TetGen
using GeometryBasics
using GeometryBasics: Mesh, QuadFace

# 四角形から立方体を構築
points = Point{3, Float64}[
    (0.0, 0.0, 0.0), (2.0, 0.0, 0.0),
    (2.0, 2.0, 0.0), (0.0, 2.0, 0.0),
    (0.0, 0.0, 12.0), (2.0, 0.0, 12.0),
    (2.0, 2.0, 12.0), (0.0, 2.0, 12.0)
]

facets = QuadFace{Cint}[
    1:4,
    5:8,
    [1,5,6,2],
    [2,6,7,3],
    [3, 7, 8, 4],
    [4, 8, 5, 1]
]

markers = Cint[-1, -2, 0, 0, 0, 0]
# 面に追加情報を付加します！
mesh = Mesh(points, meta(facets, markers=markers))
result = tetrahedralize(mesh, "vpq1.414a0.1")

using GLMakie

GLMakie.mesh(normal_mesh(result), color=(:blue, 0.1), transparency=true)
GLMakie.wireframe!(result)

```

Makieでプロットされた画像:

![image](https://user-images.githubusercontent.com/1010467/82307971-69252000-99c1-11ea-8b82-e3a206381bd3.png)

## プレーンなJulia配列を使用した例

```julia
using TetGen
let
    tetunsuitable!() do pa,pb,pc,pd
        vol=det(hcat(pb-pa,pc-pa,pd-pa))/6
        center=0.25*(pa+pb+pc+pd)-[0.5,0.5,0.5]
        vol> 0.05*norm(center)^2.5
    end

    input=TetGen.RawTetGenIO{Cdouble}()
    input.pointlist=[0 0 0;  
                     1 0 0;
                     1 1 0;
                     0 1 0;
                     0 0 1;  
                     1 0 1;
                     1 1 1;
                     0 1 1]'

    TetGen.facetlist!(input,[1 2 3 4;
                             5 6 7 8;
                             1 2 6 5;
                             2 3 7 6;
                             3 4 8 7;
                             4 1 5 8]')
    tetrahedralize(input, "pQa")
end
```

出力:

```julia
RawTetGenIO(
numberofpoints=169,
numberofedges=27,
numberoftrifaces=112,
numberoftetrahedra=809,
pointlist'=[0.0 1.0 … 0.500059730245037 0.4996534431688176; 0.0 0.0 … 0.5074057466787957 0.49707528530503103; 0.0 0.0 … 0.5033015055704277 0.4953177845338027],
tetrahedronlist'=Int32[34 47 … 15 143; 6 24 … 143 15; 58 52 … 154 150; 70 73 … 168 168],
trifacelist'=Int32[3 58 … 99 22; 19 6 … 22 8; 78 70 … 158 158],
trifacemarkerlist'=Int32[-1, -1, -1, -1, -1, -1, -1, -1, -1, -1  …  -1, -1, -1, -1, -1, -1, -1, -1, -1, -1],
edgelist'=Int32[3 5 … 70 157; 18 24 … 6 32],
edgemarkerlist'=Int32[-1, -1, -1, -1, -1, -1, -1, -1, -1, -1  …  -1, -1, -1, -1, -1, -1, -1, -1, -1, -1],
)
```

## [貢献](https://github.com/JuliaGeometry/TetGen.jl/blob/master/CONTRIBUTING.md)

## [行動規範](https://github.com/JuliaGeometry/TetGen.jl/blob/master/CODE_OF_CONDUCT.md)
