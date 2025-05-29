```
(zone, isnorth) = utm_zone(lat, lon)
(zone, isnorth) = utm_zone(ll::LatLon)
(zone, isnorth) = utm_zone(lla::LLA)
(zone, isnorth) = utm_zone(ecef::ECEF, datum)
```

与えられた緯度と経度（または世界の点）に対して、UTMゾーンと半球（`isnorth = true` または `false`）を見つけます。ノルウェーとスヴァールバルに関する特別なルールも含まれます。ゾーン0は極に対応し、UPS地域を使用します。
