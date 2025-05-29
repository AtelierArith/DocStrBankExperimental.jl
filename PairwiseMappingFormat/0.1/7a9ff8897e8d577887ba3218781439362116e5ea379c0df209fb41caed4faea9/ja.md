```
PAFRecord(buffer_size::Int)
```

単一のPAF行を表す可変型。レコードの内容はそのプロパティを通じてアクセスされます。

# 例

```jldoctest
julia> record = PAFReader(first, open(path_to_paf));

julia> record.qname
"query1"

julia> record.qlen
301156
```

参照: [`PAFReader`](@ref)

# 拡張ヘルプ

以下のプロパティが使用できます：

  * `qname::StringView`。クエリ名。空である可能性があり、`\t`および`\n`以外の任意のバイトを含むことができます。
  * `tname::Union{StringView, Nothing}`。ターゲット名。`qname`と同様ですが、レコードがマッピングされていない場合のみ`nothing`です。
  * `qlen`および`tlen::Int`は、それぞれクエリおよびターゲットシーケンスの長さを示します。これは> 0でなければなりません。
  * `qstart`、`qend`、`tstart`および`tend::Int`は、クエリおよびターゲットストランド上のアライメントの開始位置と終了位置を示します。これらは通常のJuliaの1ベースの閉区間インデックスを使用しますが、基礎となるPAF形式とは異なります。終了位置は常に開始位置以上であり、終了位置は常にクエリ/ターゲットの長さ以下です。
  * `matches::Int`は、アライメントで一致するヌクレオチド/残基の数（すなわち等しいもの）を示します。
  * `alnlen::Int`は、アライメントの長さを示します。
  * `mapq::Union{Int, Nothing}`は、マッピング品質を示し、この情報が利用できない場合は`nothing`です。
  * `is_rc::Union{Bool,Nothing}`は、クエリとターゲットストランドが互いに逆補完であるかどうかを示します。レコードがマッピングされていない場合は`nothing`です。
