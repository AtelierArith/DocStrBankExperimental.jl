```
XCBSetup
```

接続が確立されたときに受信したセットアップデータ。構造体には以下のフィールドがあります：

  * `protocol_major_version` – サーバーがサポートするXプロトコルのメジャーバージョン番号（11）
  * `protocol_minor_version` – サーバーがサポートするXプロトコルのマイナーバージョン番号（0）
  * `release_number`
  * `resource_id_base`
  * `resource_id_mask` – XIDは`resource_id_mask`のサブマスクを選択し、それを`resource_id_base`とOR演算することで生成されます
  * `motion_buffer_size` – バッファリングできるポインタ移動イベントの概算数
  * `maximum_request_length` – [`get_maximum_request_length`](@ref) ドキュメントを参照
  * `image_byte_order` – サーバーが期待する画像のバイトオーダー（`XCB_IMAGE_ORDER_LSB_FIRST`または`XCB_IMAGE_ORDER_MSB_FIRST`のいずれか）
  * `bitmap_format_bit_order` – ビットマップビットオーダー（`0`は最下位、`1`は最上位）
  * `bitmap_format_scanline_unit`
  * `bitmap_format_scanline_pad`
  * `min_keycode` – サーバーによって送信される最小のキーコード値。常に8以上
  * `max_keycode` – サーバーによって送信される最大のキーコード値。常に255以下
  * `vendor` – Xサーバーのベンダー
  * `screens` – [`XCBScreen`](@ref)を参照
  * `pixmap_formats` – [`XCBFormat`](@ref)を参照
