```
File(io::IO, header::FileHeader, signals)
```

任意の`Signal`および/または`AnnotationsSignal`のコレクションを渡すことを可能にする便利なコンストラクタです。

!!! note
    このメソッドは*コンテナ*のコピーを作成しますが、要素はコピーしません。言い換えれば、新しい`Vector{Union{Signal{T},AnnotationsSignal}}`を作成し、`signals`の内容でそれを埋めます。

