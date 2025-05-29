```
function baseddump

5 メソッド。
```

function baseddump(io::IO, data::Vector{UInt8}; base = 16, offset = 0, len = -1) function baseddump(io::IO, data; base = 16, offset = 0, len = -1) function baseddump(data; base = 16, offset = 0, len = -1)

```
`data`のダンプを（標準出力に、または指定された場合はioに）印刷します。この関数は、非UInt8データをUInt8バイトのベクターに変換しようとします。データに文字列が渡された場合、関数はこれをデータのファイル名として解釈しますので、文字列データの場合はtextdump()を使用する必要があります。ダンプされるデータの部分はデフォルトでデータ全体、または指定された場合は`offset`から`len`までです。`offset`は左側の最初の16進数の数値エントリとして印刷され、ダンプされたバイトの最終カウントは左側の最後の16進数として印刷されます。データを印刷するために使用される`base`は16（デフォルト）と2（バイナリ）の間です。データは、16および2のベースのためのunixユーティリティ`hexdump`または`xxd`の形式に似た形式でフォーマットされ、ベース10の10進形式はunixの`hexdump`に似ていますが、10進形式であり、ベース8および8進形式についても同様です。2から16の間の任意のベースがサポートされていますが、ベース2（バイナリ）、ベース8（8進）、ベース10（10進）、およびデフォルトの16（16進数）には短い関数名があります。
```

function baseddump(to::IO, from::IO; base = 16, offset = 0, len = -1) function baseddump(to::IO, filename::AbstractString; base = 16; offset = 0, len = -1)

```
ストリーム`from`またはファイル`filename`のダンプを（標準出力に、または指定された場合はIO `to`に）バイトとして印刷します。ダンプされる部分はデフォルトでeof()までのデータ全体、または指定された場合は`offset`から`len`までです。
```

これらの関数には、デフォルトでベース16の`hexdump`、デフォルトでベース2の`xxd`、デフォルトでベース10の`decdump`という短いバージョンがあります。

例:

```
hexdump("test.so")は、ファイル"test.so"の内容を16進表示で標準出力にダンプします。

xxd(stderr, s, offset = 16, length = 1008)は、s[16:16+1008-1]のバイトを、sがバイトのベクターである場合、バイナリ形式でstderrにダンプします。
```
