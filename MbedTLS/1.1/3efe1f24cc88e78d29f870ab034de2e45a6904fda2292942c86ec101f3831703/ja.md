`Cipher(info::Union{CipherID, CipherKind}) -> Cipher`

暗号オブジェクトを構築し、指定された暗号アルゴリズムを使用するように設定します。

アルゴリズムは特定のもの（例：`CIPHER_AES_256_CBC`）であるか、一般的なもの（例：`CIPHER_AES`）であることができます。後者の場合、特定の暗号のデフォルト選択が使用されます。詳細については `?CipherInfo` を参照してください。
