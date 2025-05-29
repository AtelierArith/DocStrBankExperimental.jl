```
PrefectBlock <: AbstractPrefectBlock
```

コンストラクタ:

```
PrefectBlock(blockname::String)
PrefectBlock(blockname::String, api::PrefectAPI)
PrefectBlock(blockname::String, block::AbstractPrefectBlock)
```

PrefectサーバーからPrefect Blockを返します。ブロックデータは`block`フィールドに格納されます。Prefect Blockの名前は「スラグ」と呼ばれる文字列で、`block-type-name/block-name`の形式でフォーマットされています。Prefect Blockはその名前と保存されているPrefect DBによって一意に指定されるため、コンストラクタにはAPI URLが必要です。単一引数のコンストラクタは、デフォルトのPrefectAPI()をPrefectサーバーのエンドポイントとして使用します。

サーバーでないブロックは、AbstractPrefectBlockオブジェクトを提供することで構築できます。

AbstractPrefectBlockタイプは、Prefect Python APIで定義された機能を反映することを目的としており、例えば`LocalFSBlock`には、ブロックのベースパスから相対的なパスにのみ書き込む`write_path()`メソッドが付属しています。

# 例:

```jldoctest
julia> using PrefectInterfaces

julia> spec_fsblock = LocalFSBlock("local-file-system/xanadu", "local-file-system", "/usr/mahiki/xanadu/dev");

julia> fsblock = PrefectBlock("local-file-system/xanadu", spec_fsblock);

julia> fsblock.blockname
"local-file-system/xanadu"

julia> propertynames(fsblock.block)
(:blockname, :blocktype, :basepath, :read_path, :write_path)

julia> fsblock.block.basepath
"/usr/mahiki/xanadu/dev"
```
