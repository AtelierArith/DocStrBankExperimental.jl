```
fitscollection(dir;
               recursive=true,
               abspath=true,
               keepext=true,
               ext=r"fits(\.tar\.gz)?",
               exclude=nothing,
               exclude_dir=nothing,
               exclude_key=("", "HISTORY"))
```

`dir`を走査してFITSファイルを収集し、それらのヘッダーをスキャンし、最終的に多くのファイルを反復処理して処理するために使用できる`DataFrame`にまとめます。`recursive`がfalseの場合、サブディレクトリは走査されません。

返されるテーブルには、ファイルへのパス、ファイル名、対応するHDUのインデックス、および各FITSヘッダーの列と値が含まれます。2つのFITSファイルに異なる列がある場合、適切な行に`missing`が表示されるテーブルに両方が表示されます。

!!! note "重複キー"
    特定のケースでは、同じキーを持つ複数のFITSヘッダー（例：`COMMENT`）があります。この場合、キー-値ペアの最初のインスタンスのみが保存されます。


`abspath`がtrueの場合、テーブル内のパスは絶対パスになります。`keepext`がtrueの場合、テーブル内の名前には`ext`で指定されたファイル拡張子が含まれます。`ext`は`endswith`と共に使用され、`FITSIO.FITS`と互換性のあるfitsファイルをフィルタリングします。`exclude`は、特定のファイル名を除外するために`occursin`と共に使用できるパターンです。たとえば、「sky」を含むファイルを除外するには、

```julia
fitscollection(...; exclude="sky")
```

正確なファイル名を除外するには、[正規表現文字列](https://docs.julialang.org/en/v1/manual/strings/#Regular-Expressions-1)が強力です。

```julia
fitscollection(...; exclude=r"^tek001\d")
```

最後に、[Glob.jl](https://github.com/vtjnash/Glob.jl)のような外部ツールを使用すると、さらにカスタマイズが可能です。

```julia
using Glob
fitscollection(...; exclude=fn"tek001*.fits") # 上記の正規表現マッチと同じ
```

同様に、`exclude_dir`はパターンマッチングを使用してフォルダー全体を除外することを可能にします（例：バックアップフォルダー`exclude_dir="backup"`をスキップ）。`exclude_key`は、FITSファイルの`ImageHDU`のヘッダー単位内の特定のエントリを除外することを可能にします（例：`"HISTORY"`と`""`をスキップする`exclude_key = ("HISTORY", "")`）。

ファイルのマッチングとパスの分解に関する詳細については、拡張ヘルプ（`??fitscollection`）を参照してください。

# 拡張ヘルプ

## パスの部分

`"/data"`から始まるいくつかのファイルパスを見てみましょう。これらがどのように解析されるかの例を示します。

```plain
 root  dir   base   ext
[----][---][------][---]
/data/test/tek0001.fits

 root    dir     base   ext
[----][-------][------][---]
/data/test/sci/tek0001.fits
```

`keepext`が`true`の場合、`name=base * ext`、そうでない場合は単に`base`です。`abspath`が`true`の場合、パスは`root * dir * base * ext`になります。そうでない場合は`dir * base * ext`になります。これらのオプションは、手動でファイルをフィルタリングする必要を避けるために、簡単に保存および読み込むことができるテーブルを作成する柔軟性を提供します。特に、`abspath`が、共通の構造を持つコンピュータ間やデータソース間で簡単に転送できるテーブルを保持することを可能にする方法を考慮してください。
