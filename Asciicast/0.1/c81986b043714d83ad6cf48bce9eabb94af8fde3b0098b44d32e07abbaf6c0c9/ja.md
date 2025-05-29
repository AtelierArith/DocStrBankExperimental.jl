```
Cast(file_or_io=IOBuffer(), header=Header(), start_time=time(); delay=0.0, loop=false)
```

`Cast`オブジェクトを作成し、`asciicast`ファイルを表します（フォーマットについては[https://github.com/asciinema/asciinema/blob/asciicast-v2/doc/asciicast-v2.md](https://github.com/asciinema/asciinema/blob/asciicast-v2/doc/asciicast-v2.md)を参照してください）。

  * `delay`を設定して、イベント間の一定の遅延を強制します。
  * `loop`を`true`に設定すると、連続してループします。または、指定された回数だけループする整数を設定します。これは、asciinema-playerのHTML `show`メソッドでのみサポートされています（書き込まれたファイル形式やgifサポートではサポートされておらず、現在は常にループします）。

[`write_event!`](@ref)を使用して、キャストにイベントを書き込みます。
