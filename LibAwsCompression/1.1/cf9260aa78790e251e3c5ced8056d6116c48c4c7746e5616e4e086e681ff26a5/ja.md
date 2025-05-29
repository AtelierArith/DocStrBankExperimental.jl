単一のシンボルを[`aws_huffman_code`](@ref)にエンコードするために使用される関数

# 引数

  * `symbol`:[in] エンコードするシンボル
  * `userdata`:[in] オプションのユーザーデータ ([`aws_huffman_symbol_coder`](@ref).userdata)

# 戻り値

シンボルを表すコード。もしこのシンボルが認識されない場合は、num_bitsが0に設定されたコードを返します。
