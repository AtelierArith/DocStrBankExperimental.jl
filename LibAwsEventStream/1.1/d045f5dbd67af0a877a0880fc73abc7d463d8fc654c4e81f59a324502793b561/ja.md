サーバリスナーで新しい接続が受信されたときに呼び出されます。AWS*OP*SUCCESSを返す場合は、connection_optionsのフィールドを埋める必要があります。そうしないと、プログラムはアサートして終了します。

error*codeがゼロ以外の場合、チャネルの設定中にエラーが発生し、接続はNULLになります。それ以外の場合、接続はNULLではありません。接続へのポインタを設定するつもりであれば、必ず[`aws*event*stream*rpc*server*connection*acquire`](@ref)()を呼び出し、接続が終了したら必ずaws*event*stream*server*connection*release()を呼び出す必要があります。
