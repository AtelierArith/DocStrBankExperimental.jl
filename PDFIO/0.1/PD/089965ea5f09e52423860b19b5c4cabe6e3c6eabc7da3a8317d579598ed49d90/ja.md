```
    pdDocValidateSignatures(doc::PDDoc; export_certs=false) -> Vector{Dict{Symbol, Any}}
```

## 入力

| パラメータ        | 説明                                       |
|:------------ |:---------------------------------------- |
| doc          | すべての署名を検証するための文書。                        |
| export_certs | オプションのキーワードパラメータ。設定すると、PDF文書に埋め込まれたすべての  |
|              | 証明書をエクスポートします。これらの証明書はエンドエンティティまたは1つ以上の  |
|              | 認証機関のものです。                               |
|              | 証明書はファイル`<PDF filename>.pem`にエクスポートされます。 |

## 出力

各署名に対して1つの辞書オブジェクトを表す辞書オブジェクトのベクター。辞書オブジェクトは、以下の表に従って出力にシンボルをマッピングします。

| シンボル           | 説明                       |
|:-------------- |:------------------------ |
| :Name          | 文書に署名した人または機関の名前。        |
| :P             | 署名が見つかったページのオブジェクト参照。    |
| :M             | 文書が署名されたときの`CDDate`。     |
| :certs         | 各署名オブジェクトに関連付けられた証明書。    |
| :subfilter     | PDF署名オブジェクトのサブフィルタ。      |
| :FQT           | 署名フォームの完全修飾タイトル。         |
| :chain         | 署名を検証した証明書チェーン。          |
| :passed        | 署名の検証ステータス（true / false） |
| :error_message | 検証中に返されたエラーメッセージ         |
| :stacktrace    | 検証失敗が発生した場所のスタックダンプ      |

## 注意事項

1. 証明書の信頼チェーンを検証するために必要な追加の証明書は、PEM形式で`<Package Directory>/data/certs/cacerts.pem`の*Trust Store*ファイルに手動で追加する必要があります。通常、証明書機関（ルートおよび中間）が信頼ストアに表されます。
2. *Trust Store*にエンドエンティティ証明書が存在する場合、その証明書のチェーン検証を実行する必要がないことが保証されます。ただし、これは証明書にとって良いプラクティスとは見なされません。なぜなら、証明書の検証はチェーン内のセキュリティ侵害を避けるための重要な属性だからです。CA機能を持たない自己署名証明書の場合、これが唯一の選択肢となることがあります。
3. デジタル署名の検証は、PDF Spec. 1.7のセクション12.8.1に従った承認署名の検証に制限されています。この方法では、権限および使用権の署名は検証されません。このAPIは検証レポートのみを提供します。検証出力に基づいて文書のいかなる部分へのアクセスも変更しません。APIの消費者は、アプリケーションで望ましい検証レポートに基づいて適切なアクションを取る必要があります。
4. *取り消し* - 署名が署名時属性として時間を埋め込まれている場合、または署名されたタイムスタンプまたはPDF署名辞書にM属性がある場合、それらは検証のために選択されます。ただし、取り消し情報は検証中に使用されません。
5. *PDF 2.0サポート* - サポートは実験的なもののみです。`/ETSI.CAdES.detached`のような一部のサブフィルタはサポートされていますが、文書セキュリティストア（DSS）および文書タイムスタンプ（DTS）は実装されていません。

# 例

```
julia> r = pdDocValidateSignatures(doc);

julia> r[1] # 失敗ケース
Dict{Symbol,Any} with 8 entries:
  :Name          => "JAYANT KUMAR ARORA"
  :P             => 1 0 R
  :M             => D:20190425173659+05'30
  :error_message => "Cryptoライブラリのエラー:
                        140322274480320:error:02001002:system library:..."
  :subfilter     => /adbe.pkcs7.sha1
  :stacktrace    => ["error(::String) at error.jl:33",
                     "openssl_error(::Int32) at PDCrypt.jl:96",
                     "PDFIO.PD.PDCertStore() at PDCrypt.jl:148",
                     ...]
  :FQT           => "Signature1"
  :passed        => false

julia> r[1] # 合格ケース
Dict{Symbol,Any} with 8 entries:
  :Name      => "JAYANT KUMAR ARORA"
  :P         => 1 0 R
  :M         => D:20190425173659+05'30
  :certs     => Dict{Symbol,Any}[証明書パラメータ...]
  :subfilter => /adbe.pkcs7.sha1
  :FQT       => "Signature1"
  :chain     => Dict{Symbol,Any}[証明書パラメータ...]
  :passed    => true

```
