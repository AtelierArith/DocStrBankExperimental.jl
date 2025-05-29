```
@search x [:shallow | :s | :recursive | :r]
```

インタラクティブマッチャーで `x` が定義されているファイルの場所をリストし、選択した場所をエディタで開きます。

`x` がモジュールの場合、トップレベルの定義のみが検索されます。サブモジュール内のすべての定義を検索するには、`:recursive` または `:r` フラグを渡します。

```
@search
```

式が提供されていない場合、前回の実行で返されたメソッドを検索します。すなわち、`x` は `ans` にデフォルト設定されます。

# 例

```julia
@search show                      # すべてのメソッド定義
@search @time                     # すべてのマクロ定義
@search Base.Enums                # モジュール内のメソッドとマクロ
@search REPL :r                   # モジュールを再帰的に検索
@search *(::Integer, ::Integer)   # 指定された型のメソッド
@search dot(π, ℯ)                 # 推論された型のメソッド
```

`@search` は次のように `.` や `[]` を含む複雑な式を評価し、返された値またはその型を検索することに注意してください：

```julia
@search Base.Multimedia.displays[2].repl
```
