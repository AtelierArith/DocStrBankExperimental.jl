```
EDF.TimestampedAnnotationList
```

タイムスタンプ付きアノテーションリスト (TAL) を表す型です。

この型のコンストラクタは、EDF+ 仕様に従って、与えられた `onset_in_seconds` および `duration_in_seconds` 引数を最も近い表現可能な値に丸めることを試みる場合があります。これは、a) これらの値を ASCII として表現し、b) これらの値を 8 文字の制限に制約し、c) これらのフィールドに科学的表記の使用を許可しないことを意味します。

詳細については EDF+ 仕様を参照してください。

# フィールド

  * `onset_in_seconds::Float64`: 録音開始時刻に対する発生時刻 (負の値になる場合があります)
  * `duration_in_seconds::Union{Float64,Nothing}`: この TAL の持続時間
  * `annotations::Vector{String}`: この TAL に関連付けられたアノテーション
