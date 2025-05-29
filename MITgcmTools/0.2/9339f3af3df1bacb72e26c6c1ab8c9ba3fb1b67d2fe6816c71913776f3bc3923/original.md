```
testreport(nam::String,ext="")
```

Run the testreport script for one model config `nam` (or "all"), with additional options (optional) speficied in `ext`

```
using MITgcmTools
testreport(MITgcm_config(configuration="front_relax"),"-norun")
#testreport(MITgcm_config(configuration="all"),"-norun")
```
