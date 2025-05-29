`Mechanism`を[URDF](https://wiki.ros.org/urdf/XML/model)ファイル形式にシリアライズします。

制限事項：

  * `<link>`タグについては、`<inertial>`タグのみが書き込まれ、`<visual>`および`<collision>`タグはサポートされていません。
  * `<joint>`タグについては、`<origin>`、`<parent>`、`<child>`、および`<limit>`タグのみが書き込まれ、`<calibration>`および`<safety_controller>`タグはサポートされていません。

これらの制限は、`Mechanism`がこれらのタグを書くために必要な情報を保存していないためです。

キーワード引数：

  * `robot_name`: URDFのルート`<robot>`タグの`name`属性を設定するために使用されます。デフォルト: `nothing`（name属性は設定されません）。
  * `include_root`: URDFに`root_body(mechanism)`を含めるかどうか。`false`の場合、`root_body(mechanism)`を前提とするジョイントも省略されます。デフォルト: `true`。
