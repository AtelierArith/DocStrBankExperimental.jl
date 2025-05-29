```
t = ISOtime2unix(ts::AbstractString) -> Float64
```

時間を表す文字列を受け取り、同等のUnix時間を返します。`ts`文字列は次の形式のいずれかを取ることができます：

  * "YYYY-mm-dd"、または "YYYY-mm-ddThh"、または "YYYY-mm-ddThh:mm"、または "YYYY-mm-ddThh:mm:ss"、または "dd-Jan-YY" または "dd-Jan-YYYY"

### 例

```julia
using Dates
t = ISOtime2unix("2019-01-01T12")
1.546344e9

t = ISOtime2unix("25-Apr-1974")
1.3608e8
```
