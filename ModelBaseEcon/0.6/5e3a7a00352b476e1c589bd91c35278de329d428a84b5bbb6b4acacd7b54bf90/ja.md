```
assign_parameters!(model, collection; [options])
assign_parameters!(model; [options], param=value, ...)
```

モデルパラメータに値を割り当てます。新しいパラメータは、関数呼び出しでキーと値のペアとして指定することも、`Dict`のようなコレクションで指定することもできます。

個々のパラメータは、ドット表記を使用して`model`に直接割り当てることができます。この関数は、すべてのパラメータ値がファイルから読み込まれ、辞書や他のキーと値のコレクションで利用可能な場合に、より便利です。

動作を制御する2つのオプションがあります。

  * `preserve_links=true` - `true`に設定されている場合、新しいリンクパラメータの値は無視され、リンクはそれが依存する新しいパラメータの値から自動的に更新されます。`false`に設定されている場合、リンクパラメータは上書きされ、指定された新しい値に設定された非リンクパラメータになります。
  * `check=true` - 指定された名前のパラメータが存在しない場合、それを無視します。`check`が`true`に設定されている場合、警告が発行され、`false`に設定されている場合は静かに無視されます。

また、[`export_parameters`](@ref)および[`export_parameters!`](@ref)も参照してください。

例

```
julia> @using_example E1
julia> assign_parameters(E1.model; α=0.3, β=0.7)
```
