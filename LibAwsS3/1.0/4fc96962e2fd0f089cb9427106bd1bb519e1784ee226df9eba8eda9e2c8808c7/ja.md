```
aws_s3_meta_request_write(meta_request, data, eof)
```

次のデータチャンクを書き込みます。

この関数を使用するには、`[`aws*s3*meta*request*options`](@ref).send\_using\_async\_writes`を設定する必要があります。

この関数は非同期であり、未来を返します（<aws/io/future.h>を参照）。未来が完了するまで、再度write()を呼び出すことはできません。

未来がエラーコードで完了した場合、write()は成功しなかったため、再度呼び出すべきではありません。未来にエラーコードが含まれている場合、メタリクエストはすぐに完了することが保証されます（失敗した書き込みの後にメタリクエストをキャンセルすることを心配する必要はありません）。一般的なエラーコードはAWS*ERROR*S3*REQUEST*HAS*COMPLETEDで、これはメタリクエストがwrite()呼び出しとは無関係な理由で完了したことを示します（例：CreateMultipartUploadが403 Forbiddenレスポンスを受け取った）。AWS*ERROR*INVALID*STATEは通常、write()を不正に呼び出していることを示します（例：前の書き込みが完了するのを待たずに呼び出す）。

未来が完了するまで、データをメモリに保持する必要があります。早期にメモリを解放する必要がある場合は、[`aws_s3_meta_request_cancel`](@ref)()を呼び出してください。cancel()は、保留中の書き込みからエラーコードAWS*ERROR*S3*REQUEST*HAS_COMPLETEDで未来を同期的に完了させます。

write()の呼び出し間に任意の長さの時間を待つことができます。アップロードする部分のデータが不十分な場合、データはバッファにコピーされ、未来は即座に完了します。

この関数はNULLを返すことはありません。

警告：この機能は実験的です。

# 引数

  * `meta_request`: メタリクエスト
  * `data`: 送信するデータ。データは任意のサイズで構いません。
  * `eof`: EOF（ファイルの終わり）を示すためにtrueを渡します。trueを渡した後は再度write()を呼び出さないでください。

### プロトタイプ

```c
struct aws_future_void *aws_s3_meta_request_write( struct aws_s3_meta_request *meta_request, struct aws_byte_cursor data, bool eof);
```
