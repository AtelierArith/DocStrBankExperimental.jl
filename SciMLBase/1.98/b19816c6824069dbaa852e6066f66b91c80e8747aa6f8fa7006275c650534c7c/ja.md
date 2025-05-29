`SciML.ReturnCode`

`SciML.ReturnCode` は、SciML インターフェースの標準的なリターンコード列挙型インターフェースです。リターンコードは、解法が方程式を成功裏に解決したか、方程式を解決できなかったか、そして重要なことに、なぜ終了したのかを示すためにソルバーによって与えられるノートです。

## `SciML.ReturnCode` の使用

`SciML.ReturnCode` は [EnumX.jl](https://github.com/fredrikekre/EnumX.jl) のインターフェースを使用しており、したがって EnumX のすべての動作を継承しています。これには、Enum 型自体が `SciML.ReturnCode.T` として参照され、各構成要素の列挙状態が `getproperty` を介して参照されることが含まれます。つまり、`SciML.ReturnCode.Success` です。

## 成功チェックに関する注意

インターフェースの以前のバージョンでは `sol.retcode == :Success` を使用することが推奨されていましたが、現在は推奨されておらず、代わりに `SciMLBase.successful_retcode(sol)` に置き換えるべきです。その理由は、成功と解釈できるさまざまなコードが存在するためです。例えば、`ReturnCode.Terminated` は、ユーザー指定の条件で `terminate!(integrator)` を使用して統合を終了したことを意味します。このため、`successful_retcode` はソルバーがエラーを出さなかったかどうかを照会する最も一般的な方法です。

## プロパティ

  * `successful_retcode(retcode::ReturnCode.T)`: 出力列挙型がソルバーの成功状態と見なされるかどうかを判断します。つまり、ソルバーが方程式を成功裏に解決したかどうかです。`ReturnCode.Success` は最も基本的な形式で、単に成功したことを宣言しますが、より多くの情報を提供する成功リターンコードも存在します。
