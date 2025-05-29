補足属性を格納する構造体のベースタイプ

サブタイプに必要なインターフェース関数：

  * get_internal()

オプションのインターフェース関数：

  * get_uuid()

サブタイプは時系列を含むことができ、これには

  * `supports_time_series(::SupplementalAttribute)`

が必要です。

すべてのサブタイプは、各属性に付随するコンポーネントを追跡するために、ComponentUUIDsのインスタンスを含める必要があります。
