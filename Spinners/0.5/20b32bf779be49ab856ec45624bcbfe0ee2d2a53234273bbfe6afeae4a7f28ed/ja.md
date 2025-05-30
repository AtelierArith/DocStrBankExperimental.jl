`@spinner`: Unicodeサポートを持つコマンドラインスピナー

使用法: `@spinner [style] [rate] [message] function`

  * `style`: `String`、`Vector{String}`、または`Symbol`

      * サポートされているシンボルのリストについては`Spinners.list`を参照してください
  * `rate`: フレームあたりの秒数
  * `message::String`: スピナーの右側に表示されるテキスト

例:

```
	@spinner
	@spinner :aesthetic
	@spinner "◧◨" 0.5 sleep(5)
```
