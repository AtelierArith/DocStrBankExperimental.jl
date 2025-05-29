```
parse_ldraw_file(filename)
parse_ldraw_file(filename; sneaky_parts::Set{String}=preprocess_ldraw_file(filename),
ignore_rotation_determinant::Bool=false)
```

LDrawファイルを解析し、MPDModelを返します。ファイルは.mpdまたは.ldrファイルです。

# キーワード引数:

  * `sneaky_parts::Set{String}`: サブモデルとして偽装されている部品名のセット。

この引数を含める必要はほとんどなく、`preprocess_ldraw_file`によって自動的に生成されます。(デフォルト: `preprocess_ldraw_file(filename)`)

  * `ignore_rotation_determinant::Bool`: trueの場合、回転行列の行列式を無視します。一部の部品は負の行列式を持つ回転行列を持っています。これはレンダリングには影響しませんが、他の操作に問題を引き起こす可能性があります。(デフォルト: false)
