```
listecmwfvars(source::Symbol=:reanalysis; single::Bool=true, levlist::Bool=false, contain::AbstractString="")
```

CDS ERA5変数のリストを印刷します。

### 引数

  * `source`: データのソース。$:reanalysis$または$:forecast$のいずれかです。デフォルトは`:reanalysis`です。

### キーワード引数

  * `single`: trueの場合、単一レベルの変数のみがリストされます。falseの場合、圧力レベルの変数がリストされます [デフォルトはtrueです]。
  * `pressure`: trueの場合、圧力レベルの変数のみがリストされます。falseの場合、単一レベルの変数がリストされます。
  * `contain`: 変数の名前でフィルタリングするための文字列。この文字列を含む変数のみがリストされます（大文字と小文字を区別します）。提供されない場合、すべての変数がリストされます。

#### 例

```julia
# すべての圧力レベルの変数を印刷します。
listecmwfvars(pressure=true)

# 予報データセットから名前に「Temperature」を含む単一レベルの変数のみを印刷します。
listecmwfvars(:forecast, contain="Temperature")
```
