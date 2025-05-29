```
restore_from_db(db::ExperimentDatabase, experiment::Experiment)
```

Searches the `db` for the supplied experiment, matching on the configuration and the name, disregarding the unique ID.

If experiment already exists in the db, returns that experiment with the db's UUID for it, otherwise return the input experiment.

Will error if the experiment exists but does not match the input experiment configuration.
