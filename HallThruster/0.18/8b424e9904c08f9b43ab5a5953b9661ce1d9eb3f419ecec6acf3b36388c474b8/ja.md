```julia
struct Thruster
```

名前、幾何学、磁場からホールスラスターを定義します。スラスターはシールドされている場合もあり、その場合、壁の電子温度は放電チャネル内の陽極電子温度と等しいと仮定されます。

# フィールド

  * `name::String`: スラスターの名前。シミュレーション中には使用されませんが、特定のケースでは便利です。
  * `geometry::HallThruster.Geometry1D`: スラスターの幾何学
  * `magnetic_field::HallThruster.MagneticField`: 離散的な軸方向位置での磁場を含みます
  * `shielded::Bool`: スラスターが磁気シールドされているかどうか
