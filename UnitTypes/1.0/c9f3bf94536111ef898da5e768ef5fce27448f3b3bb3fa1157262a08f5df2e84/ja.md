`macro relateMeasures(relation)`

左辺と右辺の間に乗法的関係を追加し、一貫した単位で単位を掛け算および割り算できるようにします。すべての型はすでに定義されている必要があり、左辺では1つの*のみがサポートされ、右辺は結果の型である必要があります。

`@relateMeasures Meter*Newton = NewtonMeter`
