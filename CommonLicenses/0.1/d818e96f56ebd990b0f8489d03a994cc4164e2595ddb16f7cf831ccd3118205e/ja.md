オープンソースソフトウェア（およびその他の）ライセンスを実行可能なドキュメント内にインライン表示しましょう！

# 拡張ヘルプ

## README

[![Tests](https://github.com/cadojo/CommonLicenses.jl/workflows/UnitTests/badge.svg)](https://github.com/cadojo/CommonLicenses.jl/actions?query=workflow%3AUnitTests) [![Docs](https://github.com/cadojo/CommonLicenses.jl/workflows/Documentation/badge.svg)](https://cadojo.github.io/CommonLicenses.jl/dev)

# `CommonLicenses.jl`

*実行可能なドキュメントのための実行可能なライセンス！*

## インストール

*以下の行のいずれかを選択してください！*

```julia
import Pkg; Pkg.add("CommonLicenses")
```

```julia
# Julia REPL で
]add CommonLicenses
```

## 動機

*なぜこれが存在するのか？*

ブログ記事を書いていると想像してみてください。あるいは [Pluto](https://plutojl.org) ノートブック。あるいは [Jupyter](https://jupyter.org) ノートブック。あるいは何でも！あなたはコンテンツとともに言葉を書いていて、あなたの作品にライセンスを付与したいと思っています。ライセンスはあなたのドキュメントと*独立して*存在する必要があります。「素朴な」解決策は、標準ライセンスファイルの内容を見つけて、そのライセンスをドキュメントのどこかのテキストブロックに貼り付けることです。クールですね。2週間後、あなたは*別の*ブログ記事を書いています、あるいは何でも。あなたはこのライセンスの内容を再度見つける必要があります。大したことではありませんが、これが少し面倒になりますよね？

そこで登場するのが `CommonLicenses.jl` です。このパッケージは、[SPDXライセンスリスト](https://spdx.org/licenses/)によって追跡されるすべての標準ライセンスを提供しますので、このパッケージをインストールし、希望するライセンスを好きな場所に印刷するだけで済みます！

## 使用法

*自分で試してみてください！*

```julia
julia> using CommonLicenses

julia> using CommonLicenses: MIT, Unlicense

julia> MIT()

julia> Unlicense()

julia> CommonLicenses.text(MIT(copyright="Joe(y)"))

julia> CommonLicenses.name(License("CC-BY-4.0"))
```

## クレジット

*多くの役立つプロジェクトの上に構築されています！*

このパッケージは [`PkgLicenses.jl`](https://github.com/JuliaPackaging/PkgLicenses.jl/tree/master) とは独立して開発されましたが、`JuliaPackaging` が先に到達したようです！このパッケージは、`PkgLicenses.jl` の機能に加えて、`MIME` タイプのサポートや、クリエイティブ・コモンズなどの非ソフトウェアプロジェクトのライセンスを追加しています。

[SPDXライセンスリスト](https://spdx.org/licenses/) は、要求された各ライセンスの内容を取得するために使用されます。GitHubの[ライセンスAPI](https://docs.github.com/en/rest/licenses)は、利用可能な場合、各ライセンスの追加メタデータを見つけるために使用されます。

## ライセンス

MITライセンス

Copyright (c) 2023 Joe Carpinelli

本ソフトウェアおよび関連する文書ファイル（以下「ソフトウェア」）のコピーを取得したすべての人に対し、無償で、ソフトウェアを制限なく取り扱う権利が付与されます。これには、使用、コピー、変更、統合、出版、配布、サブライセンス、及び/またはソフトウェアのコピーを販売する権利が含まれ、ソフトウェアが提供される人々にも同様の権利を許可するものとします。ただし、以下の条件に従うものとします。

上記の著作権表示およびこの許可表示は、ソフトウェアのすべてのコピーまたは重要な部分に含まれるものとします。

ソフトウェアは「現状のまま」提供され、いかなる種類の保証もなく、明示または暗示を問わず、商品性、特定の目的への適合性、及び非侵害に関する保証を含みますが、これに限定されません。著者または著作権者は、ソフトウェアまたはソフトウェアの使用またはその他の取引に起因するいかなる請求、損害、またはその他の責任についても責任を負わないものとします。

## エクスポート

  * [`License`](@ref)

## インポート

  * `Base`
  * `Core`
  * `Dates`
  * `DocStringExtensions`
  * `HTTP`
  * `JSON`
  * `Scratch`
