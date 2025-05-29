```
open_db(database_name, [experiment_folder, create_folder]; in_memory=false)
```

Opens a database and prepares it with the Experimenter.jl schema with tables for Experiment, Trial and Snapshot. If the database already exists, it will open it and not overwrite the existing data.

Setting `in_memory` to `true` will skip all of the arguments and create the database "in memory" and hence, will not persist.
