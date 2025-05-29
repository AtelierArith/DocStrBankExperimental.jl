```
loadrxnetwork(ft::BNGNetwork, rxfilename; name = gensym(:ReactionSystem), verbose = false, kwargs...)
```

BioNetGenの`.net`ファイルを解析し、`ParsedReactionNetwork`オブジェクトを構築します。

# 引数

  * `ft::BNGNetwork`: 解析するファイルがBioNetGenの".net"ファイルであることを示します。
  * `rxfilename::String`: 解析する`.net`ファイルへのパス。
  * `name::Symbol`: （オプション）結果の`ReactionSystem`の名前。生成されたシンボルがデフォルトです。
  * `verbose::Bool`: （オプション）`true`の場合、解析中に詳細な進行情報を印刷します。デフォルトは`true`です。
  * `kwargs...`: `ReactionSystem`コンストラクタに渡される追加のキーワード引数。

# 戻り値

以下を含む`ParsedReactionNetwork`オブジェクト：

  * 反応、種、およびパラメータを持つ`ReactionSystem`。
  * 初期条件（`u0`）およびパラメータ値（`p`）。
  * 変数名とシンボルの間のマッピング。

# 注意事項

この関数はBioNetGenの`.net`ファイル形式のサブセットを解析します。以下を前提としています：

  * 式はJuliaの構文と互換性があります。
  * 時間依存または条件付きロジックはサポートされていません。
  * より複雑な関数構造はサポートされていない可能性があります。

# 例

```julia
parsed_network = loadrxnetwork(BNGNetwork(), "path/to/network.net", verbose = true)
```
