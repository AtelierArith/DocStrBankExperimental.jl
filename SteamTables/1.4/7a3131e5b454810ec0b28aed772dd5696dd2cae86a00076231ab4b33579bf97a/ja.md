# SteamTables

IAPWS-97 工業用定式 水と蒸気の特性。P&T、P&h、またはP&sの入力に基づいて、ギブズ自由エネルギー、ヘルムホルツ自由エネルギー、エンタルピー、エントロピー Cp、Cv、および音速を提供します。

## エクスポートされた関数:

### 単一入力:

Psat(T) および Tsat(P) は飽和温度または圧力を返します   SatDensL(T) および SatDensV(T) は飽和密度を返します   SatHL(T) および SatHV(T) は飽和エンタルピーを返します   SatSL(T) および SatSV(T) は飽和エントロピーを返します   DeltaHvap(T) は蒸発の潜熱を返します

### 二つの入力:

P と T   SpecificG,    SpecificF,     SpecificV,     SpecificU,      SpecificS,   SpecificH,    SpecificCP,    SpecificCV,    SpeedOfSound

P と h   SpecificG*Ph, SpecificF*Ph,  SpecificV*Ph,  SpecificU*Ph,   SpecificS*Ph,   SpecificH*Ph, SpecificCP*Ph, SpecificCV*Ph, SpeedOfSound*Ph   Quality*Ph, Temperature_Ph

P と s   SpecificG*Ps, SpecificF*Ps,  SpecificV*Ps,  SpecificU*Ps,   SpecificS*Ps,   SpecificH*Ps, SpecificCP*Ps, SpecificCV*Ps, SpeedOfSound*Ps   Quality*Ps, Temperature_Ps

T と h   Quality_Th

T と s   Quality_Ts

SpecificG    [kJ/kg]  特定のギブズ自由エネルギー SpecificF    [kJ/kg]  特定のヘルムホルツ自由エネルギー SpecificV    [m3/kg]  特定の体積 SpecificU    [kJ/kg]  特定の内部エネルギー SpecificS    [kJ/kgK] 特定のエントロピー SpecificH    [kJ/kg]  特定のエンタルピー SpecificCp   [kJ/kgK] 特定の定圧比熱容量 SpecificCv   [kJ/kgK] 特定の定容比熱容量 SpeedOfSound [m/s]    音速

デフォルトでは温度はK、圧力はMPaです。

入力にUnitful.jlを介して単位が関連付けられている場合、返される値にもデフォルトの単位が関連付けられます。これらは呼び出し関数内で好みの単位に変換できます。

## エクスポートされた定数   R  = 0.461526   [kJ/kg/K] 普遍気体定数   Tc = 647.096    [K]       水の臨界温度   Pc = 22.064     [MPa]     水の臨界圧力   ρc = 322.       [kg/m3]   水の臨界密度   T3 = 273.16     [K]       水の三重点温度   P3 = 611.657E-6 [MPa]     水の三重点圧力   Mr = 18.01528   [kg/kmol] 水の分子量

エクスポートされた定数には関連する単位がありません。単位は簡単に追加できます、   例:

Ru = R * 1.0u"kJ/kg/K"
