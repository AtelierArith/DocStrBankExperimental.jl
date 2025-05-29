```
extractarchiveprogress(client::PCloudClient; kwargs...)
```

アーカイブ抽出プロセスの出力と完了ステータスを返します。

`extractarchive`によって返された`progresshash`をパラメータとして期待し、オプションで`lines`を指定します。

ブール値`finished`は、プロセスが完了したかどうかを示します。`output`配列には、抽出プログラムの出力行が返されます。`lines`の数はこのメソッドに戻すことができ、すでに返された出力行を除外します。

Source: https://docs.pcloud.com/methods/archiving/extractarchiveprogress.html

# オプション引数

  * `lines::Int`: 出力配列からスキップする出力行の数

# 出力

上記の通りです。

# 出力例

```
{
  "result": 0,
  "lines": 109,
  "finished": true,
  "output": [
    "Titov.zip: Zip",
    "  Titov/_ART5055.jpg  (1681557 B)... OK.",
    "  Titov/_ART5059.jpg  (1713601 B)... OK.",
    "  Titov/_ART5063.jpg  (1811854 B)... OK.",
    "  Titov/_ART5069.jpg  (1918700 B)... OK.",
    "  Titov/_ART5071.jpg  (1701381 B)... OK.",
    "  Titov/_ART5074.jpg  (1678731 B)... OK.",
    "  Titov/_ART5076.jpg  (1658403 B)... OK.",
    "  Titov/_ART5079.jpg  (1728540 B)... OK.",
    "  Titov/_ART5094.jpg  (1745843 B)... OK.",
    "  Titov/_ART5102.jpg  (1716455 B)... OK.",
    "  Titov/_ART5103.jpg  (1616031 B)... OK.",
    "  Titov/_ART5626.jpg  (2174388 B)... OK.",
    "  Titov/_ART5628.jpg  (2061103 B)... OK.",
    "  Titov/_ART5864.jpg  (1490067 B)... OK.",
    "  Titov/_ART5866.jpg  (1503272 B)... OK.",
    "  Titov/_ART5868.jpg  (1748141 B)... OK.",
    "  Titov/_ART5869.jpg  (1839470 B)... OK.",
    "  Titov/_ART5878.jpg  (1264889 B)... OK.",
    "  Titov/_ART6108.jpg  (2190771 B)... OK.",
    "  Titov/_ART6109.jpg  (2019572 B)... OK.",
    "  Titov/_ART6111.jpg  (1939203 B)... OK.",
    "  Titov/_ART6118.jpg  (2279575 B)... OK.",
    "  Titov/_ART6123.jpg  (2204205 B)... OK.",
    "  Titov/_ART6366.jpg  (2135242 B)... OK.",
    "  Titov/_ART6368.jpg  (2287593 B)... OK.",
    "  Titov/_ART6375.jpg  (2191877 B)... OK.",
    "  Titov/_MG_2238.jpg  (1466355 B)... OK.",
    "  Titov/_MG_2244.jpg  (1295216 B)... OK.",
    "  Titov/_MG_2246.jpg  (1460799 B)... OK.",
    "  Titov/_MG_2248.jpg  (1529065 B)... OK.",
    "  Titov/_MG_2253.jpg  (1227511 B)... OK.",
    "  Titov/_MG_2254.jpg  (1480305 B)... OK.",
    "  Titov/_MG_3035.jpg  (1789125 B)... OK.",
    "  Titov/_MG_3164.jpg  (1952735 B)... OK.",
    "  Titov/_MG_3170.jpg  (1063317 B)... OK.",
    "  Titov/_MG_3172.jpg  (2357181 B)... OK.",
    "  Titov/_MG_3173.jpg  (2142821 B)... OK.",
    "  Titov/_MG_3885.jpg  (1311330 B)... OK.",
    "  Titov/_MG_3890.jpg  (1925228 B)... OK.",
    "  Titov/_MG_3892.jpg  (1797677 B)... OK.",
    "  Titov/_MG_3899.jpg  (2225951 B)... OK.",
    "  Titov/_MG_4108.jpg  (1341266 B)... OK.",
    "  Titov/_MG_4409.jpg  (1826640 B)... OK.",
    "  Titov/_MG_4416.jpg  (1312750 B)... OK.",
    "  Titov/_MG_5430.jpg  (1888501 B)... OK.",
    "  Titov/_MG_5458.jpg  (2223461 B)... OK.",
    "  Titov/_MG_5640.jpg  (1850502 B)... OK.",
    "  Titov/_MG_5645.jpg  (1315393 B)... OK.",
    "  Titov/_MG_5646.jpg  (1453218 B)... OK.",
    "  Titov/_MG_5653.jpg  (1448595 B)... OK.",
    "  Titov/_MG_5654.jpg  (1461125 B)... OK.",
    "  Titov/_MG_6130.jpg  (2272260 B)... OK.",
    "  Titov/_MG_6137.jpg  (1042867 B)... OK.",
    "  Titov/_MG_6139.jpg  (1001587 B)... OK.",
    "  Titov/_MG_6147.jpg  (1968840 B)... OK.",
    "  Titov/_MG_6154.jpg  (2471284 B)... OK.",
    "  Titov/_MG_6197.jpg  (1935389 B)... OK.",
    "  Titov/_MG_6200.jpg  (1952539 B)... OK.",
    "  Titov/_MG_6204.jpg  (1547425 B)... OK.",
    "  Titov/_MG_6213.jpg  (1863369 B)... OK.",
    "  Titov/_MG_6227.jpg  (1751445 B)... OK.",
    "  Titov/_MG_6238.jpg  (1530810 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0007.jpg  (3422222 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0010.jpg  (3695719 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0094.jpg  (3521664 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0095.jpg  (2429226 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0096.jpg  (2488633 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0097.jpg  (2655423 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0098.jpg  (2340300 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0099.jpg  (2568207 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0101.jpg  (3147384 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0231.jpg  (1926706 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0238.jpg  (1559040 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0246.jpg  (1869346 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0250.jpg  (1458431 B)... OK.",
    "  Titov/Rally_Sliven_2013_FRI_0251.jpg  (1031734 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0038.jpg  (3613789 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0039.jpg  (3723149 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0040.jpg  (3262341 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0042.jpg  (2788097 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0200.jpg  (3643640 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0201.jpg  (2680875 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0202.jpg  (2544499 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0203.jpg  (2840461 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0204.jpg  (2700571 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0205.jpg  (2631643 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0206.jpg  (2409407 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0345.jpg  (2655096 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0346.jpg  (3268206 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0347.jpg  (2035836 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0348.jpg  (2284103 B)... OK.",
    "  Titov/Rally_Sliven_2013_SAT_0349.jpg  (2071153 B)... OK.",
    "  Titov/Rally_Sliven_2013_SUN_0041.jpg  (2340276 B)... OK.",
    "  Titov/Rally_Sliven_2013_SUN_0042.jpg  (2950695 B)... OK.",
    "  Titov/Rally_Sliven_2013_SUN_0043.jpg  (2526685 B)... OK.",
    "  Titov/Rally_Sliven_2013_SUN_0044.jpg  (2051779 B)... OK.",
    "  Titov/TJP_6400.jpg  (1127206 B)... OK.",
    "  Titov/TJP_6425.jpg  (1239689 B)... OK.",
    "  Titov/TJP_6797.jpg  (1858359 B)... OK.",
    "  Titov/TJP_6799.jpg  (3042033 B)... OK.",
    "  Titov/TJP_7114.jpg  (1375604 B)... OK.",
    "  Titov/TJP_7120.jpg  (1332261 B)... OK.",
    "  Titov/TJP_7126.jpg  (2182860 B)... OK.",
    "  Titov/TJP_7127.jpg  (1519095 B)... OK.",
    "  Titov/TJP_7541.jpg  (2216513 B)... OK.",
    "  Titov/TJP_7867.jpg  (1076556 B)... OK.",
    "  Titov/TJP_7873.jpg  (1079839 B)... OK.",
    "Successfully extracted to current directory."
  ]
}
```
