```
EventParameters(; comment, event, description, creation_info, public_id)
```

QuakeMLのルートタイプ。 `EventParameters`オブジェクトは一連のイベントを含み、QuakeML XMLファイルには1つの`EventParameters`オブジェクトのみを含めることができます。

公報タイプ（非リアルタイム）モデルでは、このタイプは`Event`オブジェクトのコンテナとして機能します。リアルタイムバージョンでは、`Event`、`Origin`、`Magnitude`、`StationMagnitude`、`FocalMechanism`、`Reading`、`Amplitude`、および`Pick`タイプのオブジェクトを保持できます。

# フィールドのリスト

  * `event :: Vector{Event}`: カタログまたはイベントのコレクションを構成する[`Event`](@ref QuakeML.Event)のセット。
  * `description :: String`: 地震カタログまたはイベントのコレクションに割り当てることができる説明文字列。
  * `comment :: Vector{Comment}`: 追加のコメント。
  * `creation_info :: CreationInfo`: 地震カタログのための[`CreationInfo`](@ref QuakeML.CreationInfo)。
  * `public_id :: ResourceReference`: `EventParameters`のリソース識別子。(**必須フィールド。**)

!!! note
    現在、QuakeML.jlは非リアルタイムバージョンのQuakeMLのみをサポートしています。

