```
testreport(config::MITgcm_config,ext="")
```

Run the testreport script for one model `config`, with additional options specified in `ext` if needed.

```
using MITgcm
testreport(MITgcm_config(configuration="front_relax"))
#testreport(MITgcm_config(configuration="front_relax"),"-norun")
```
