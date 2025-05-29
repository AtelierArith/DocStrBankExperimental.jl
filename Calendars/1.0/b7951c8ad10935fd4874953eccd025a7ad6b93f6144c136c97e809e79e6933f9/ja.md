CDate（カレンダー日付の略）は次のように定義されます。

```julia
CDate = Tuple{DPart, DPart, DPart, DPart}
```

```
型 `CDate` のタプル `date` は、慣例として
(calendar, year, month, day) のように展開されます。ここで `calendar` は次のいずれかです。
```

```julia
"European" 
"Common" 
"Julian" 
"Hebrew" 
"Islamic" 
"IsoDate"
```

```
また、次の略語を使用することもできます。
```

```julia
EC, CE, JD, AM, AH, and ID 
```

```
「Common」または CE は、先行グレゴリオ暦を示し、`DPart`（日付部分）は Int64 の型名です。
```

```julia
CDateStr(cd::CDate) 
```

関数 CDateStr は、型 CDate の日付を文字列表現に変換します。このとき、数値部分は ISO 8601 の推奨に従い、上記のカレンダー名の略語のいずれかで接頭辞が付けられます。

`CDates` とそれに対する `CDateStr` によって与えられる文字列表現の例：

```julia
("European", 2022,  1,  6)  -> "EC-2022-01-06"
("Common",   2022,  1, 19)  -> "CE-2022-01-19"
("Julian",   2022,  1,  6)  -> "JD-2022-01-06"
("Hebrew",   5782, 11, 17)  -> "AM-5782-11-17"
("Islamic",  1443,  6, 15)  -> "AH-1443-06-15"
("IsoDate",  2022,  3,  3)  -> "ID-2022-03-03"
```

`CDate` のコンポーネントには、次の関数を適用することでアクセスできます。

```julia
Calendar, Year, Month, Day and Date 
```

カレンダー日付に対して。

関数 CalendarName(CC) は、カレンダー指定子 CC からカレンダー名を返します。たとえば、CalendarName(ID) と CalendarName(6) の両方は、文字列 "IsoDate" を返します。
