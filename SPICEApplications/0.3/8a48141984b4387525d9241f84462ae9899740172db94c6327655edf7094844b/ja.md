すべてのSPICEユーティリティをJulia内から呼び出そう！

!!! warning
    このパッケージはNASA、JPL、Caltech、または他のいかなる組織とも提携していないか、承認されていません！これは、天体力学の愛好家によって独自に書かれたパッケージです。


# 拡張ヘルプ

## README

[![Tests](https://github.com/cadojo/SPICEApplications.jl/workflows/UnitTests/badge.svg)](https://github.com/cadojo/SPICEApplications.jl/actions?query=workflow%3AUnitTests) [![Docs](https://github.com/cadojo/SPICEApplications.jl/workflows/Documentation/badge.svg)](https://cadojo.github.io/SPICEApplications.jl) [![SciML Code Style](https://img.shields.io/static/v1?label=Style&message=SciML&color=9668e2&labelColor=3E474F)](https://github.com/SciML/SciMLStyle)

# `SPICEApplications`

*NASA JPLの`SPICEApplications`プログラムを使用して、すべてをJulia内でエフェメリスカーネルファイルを生成します！*

**`v1.0`まではすべての小さな変更が破壊的であると考えてください！**

> **警告**
>
> このパッケージはNASA、JPL、Caltech、または他のいかなる組織とも提携していないか、承認されていません！これは、天体力学の愛好家によって独自に書かれたパッケージです。


## インストール

次の2行のいずれかを選択してください！

```julia
import Pkg; Pkg.add("SPICEApplications");
```

```julia
]add SPICEApplications # JuliaのREPLで
```

## クレジット

NASA JPLは、`SPICEApplications`を含む[NAIF SPICE Toolkit](https://naif.jpl.nasa.gov/naif/toolkit.html)を開発および維持しています。Helge Eichhornは[`SPICE.jl`](https://github.com/JuliaAstro/SPICE.jl)を開発および維持しており、SPICE Toolkitの周りの[Juliaラッパー](https://juliahub.com/ui/Packages/CSPICE_jll/XJqVo/67.0.0+0)も提供しています。

## ライセンス

MITライセンス

Copyright (c) 2023 Joe Carpinelli

このソフトウェアおよび関連する文書ファイル（以下「ソフトウェア」といいます）のコピーを取得したすべての人に対して、無償で、ソフトウェアを制限なく取り扱う権利を付与します。これには、使用、コピー、変更、統合、出版、配布、サブライセンス、及び/またはソフトウェアのコピーを販売する権利が含まれ、ソフトウェアが提供される人々に対しても同様の権利を許可します。ただし、以下の条件に従うものとします。

上記の著作権表示およびこの許可表示は、ソフトウェアのすべてのコピーまたは重要な部分に含めるものとします。

ソフトウェアは「現状のまま」提供され、いかなる種類の保証もなく、明示的または暗示的な保証、商品性、特定の目的への適合性、及び非侵害を含みますが、これに限定されません。著者または著作権者は、ソフトウェアまたはソフトウェアの使用またはその他の取引に起因するいかなる請求、損害、またはその他の責任についても責任を負わないものとします。

## エクスポート

  * [`brief`](@ref)
  * [`chronos`](@ref)
  * [`ckbrief`](@ref)
  * [`commnt`](@ref)
  * [`dskbrief`](@ref)
  * [`dskexp`](@ref)
  * [`frmdiff`](@ref)
  * [`inspekt`](@ref)
  * [`mkdsk`](@ref)
  * [`mkspk`](@ref)
  * [`msopck`](@ref)
  * [`spacit`](@ref)
  * [`spkdiff`](@ref)
  * [`spkmerge`](@ref)
  * [`tobin`](@ref)
  * [`toxfr`](@ref)

## インポート

  * `Base`
  * `Core`
  * `DocStringExtensions`
