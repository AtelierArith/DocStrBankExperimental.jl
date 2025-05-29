オプションのコールバックで、アップロードが完了する前にレビューすることができます。たとえば、各パートのチェックサムを確認し、同意しない場合はアップロードを失敗させることができます。

リクエストの処理を続行するには、AWS*OP*SUCCESSを返します。

リクエストをキャンセルするには、aws*raise*error(E)を返します。あなたが発生させるエラーは、`[`aws*s3*meta*request*result`](@ref).error\_code`に反映されます。どのエラーを発生させるべきかわからない場合は、AWS*ERROR*S3_CANCELEDを使用してください。

警告: この機能は実験的/不安定です。この時点では、コールバックはマルチパートアップロードのみに呼び出されます（Content-Lengthが`multipart_upload_threshold`を超える場合、またはContent-Lengthが指定されていない場合）。

# 引数

  * `meta_request`: アップロードの[`aws_s3_meta_request`](@ref)へのポインタ。
  * `info`: アップロードに関する詳細情報。
