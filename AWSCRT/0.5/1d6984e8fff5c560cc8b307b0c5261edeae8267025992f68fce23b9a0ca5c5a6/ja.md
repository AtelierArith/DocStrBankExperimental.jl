```
ShadowFramework(
    connection::MQTTConnection,
    thing_name::String,
    shadow_name::Union{String,Nothing},
    shadow_document::T;
    shadow_document_property_callbacks::Dict{String,ShadowDocumentPropertyUpdateCallback} = Dict{
        String,
        ShadowDocumentPropertyUpdateCallback,
    }(),
    shadow_document_pre_update_callback::ShadowDocumentPreUpdateCallback = (v) -> nothing,
    shadow_document_post_update_callback::ShadowDocumentPostUpdateCallback = (v) -> nothing,
    id = 1,
) where {T}
```

`ShadowFramework`を作成します。

引数:

  * `connection (MQTTConnection)`: 接続。
  * `thing_name (String)`: シャドウドキュメントが存在するAWS IoTのThingの名前。
  * `shadow_name (Union{String,Nothing})`: 名前付きシャドウドキュメントのためのシャドウ名、または名前のないシャドウドキュメントのための`nothing`。
  * `shadow_document (AbstractDict)`: ローカルシャドウドキュメント。これは、ブローカーによって公開されたシャドウドキュメントのすべてのキーを含む必要があります。また、シャドウドキュメントのバージョンを格納する`version (Int)`キーも含む必要があります。これをディスクに永続化することをお勧めします。`shadow_document_post_update_callback`内で最新の状態をディスクに書き込むことができます。また、アプリケーションの開始時にディスクから読み込み、このパラメータとして渡す必要があります。
  * `shadow_document_property_callbacks (Dict{String,ShadowDocumentPropertyUpdateCallback})`: オプションのコールバックのセット。指定されたキーに一致するシャドウドキュメントプロパティの各更新に対して、指定されたコールバックが発火します。シャドウプロパティが変更されたときのみコールバックが発火することに注意してください。シャドウプロパティの変更は、シャドウプロパティの値が以前の値と等しくない新しい値に変更されたときに発生します。これは`!isequal()`を使用して実装されています。シャドウドキュメントで使用されるすべての型に対して、アプリケーションのニーズに満足する`isequal`の定義を確保してください。カスタムJSONデシリアライズを使用している場合にのみ、これを心配する必要があります。
  * `shadow_document_pre_update_callback (ShadowDocumentPreUpdateCallback)`: シャドウドキュメントプロパティを更新する直前に発火するオプションのコールバック。シャドウプロパティが変更されない場合でも、常に発火します。
  * `shadow_document_post_update_callback (ShadowDocumentPostUpdateCallback)`: シャドウドキュメントプロパティを更新した直後に発火するオプションのコールバック。シャドウプロパティが変更された場合にのみ発火します。
  * `shadow_document_property_pre_update_funcs (Dict{String,ShadowDocumentPropertyPreUpdateFunction})`: 特定のシャドウドキュメントプロパティの更新動作をカスタマイズするオプションの関数のセット。詳細については[`ShadowDocumentPropertyPreUpdateFunction`](@ref)を参照してください。
  * `id (Int)`: 複数のシャドウフレームワークからのログメッセージを区別する一意のID。

他に[`ShadowDocumentPropertyUpdateCallback`](@ref)、[`ShadowDocumentPreUpdateCallback`](@ref)、[`ShadowDocumentPostUpdateCallback`](@ref)、[`MQTTConnection`](@ref)を参照してください。

```
!!! note "制限事項"
    プロパティの望ましい値を`null`に設定することによってプロパティを削除することは現在サポートされていません。AWS IoTはその`null`プロパティを望ましい状態から削除しますが、プロパティは報告された状態に残ります。
```
