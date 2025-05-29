```
crc(spec[, tables = Multiple])
```

`tables`のルックアップテーブル動作を持つ`spec`を実装するcrc関数を作成します。利用可能な仕様は[`ALL`](@ref)にリストされており、テーブルは[`Multiple`](@ref)、[`Single`](@ref)または[`NoTables`](@ref)のいずれかです。

返される関数は`String`、`Vector{UInt8}`または`IO`を受け入れ、CRCチェックサムを計算します。オプションのブールパラメータ`append`は、チェーン適用のために使用できます。

より高速なCRC32*C*実装はStdlibにあります: [`CRC32c`](@ref)。

# 例

```julia-repl
using CRC

# 自分のcrc関数を一度だけ作成
crc32 = crc(CRC_32)

# 上で作成したcrc関数を何度も使用
for s in ["hello", "there"]
    println(s => crc32(s))
end
```
