function get*ashp*defaults(load_served::String="SpaceHeating")

ASHPのデフォルトをJSONデータファイルから取得します。

inputs load*served::String – AHSPシステムによって供給される暖房負荷の識別子 force*into_system::Bool – 互換性のある熱負荷のみを専用に供給する場合はtrue（すなわち、既存の技術を置き換えます）

returns ashp_defaults::Dict – ASHPのデフォルトを含む辞書
