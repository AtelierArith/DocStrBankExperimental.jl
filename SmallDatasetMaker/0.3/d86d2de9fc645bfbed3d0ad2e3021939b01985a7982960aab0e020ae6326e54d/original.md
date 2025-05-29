`unzip_file(target_path)` unzip file at `target_path` to current directory preserve its original name.

# Notice!

If you were intended to load `target_path` under `SmallDatasetMaker` or anyother package rather than the current directory you are working with, you should apply `abspath(args::String...)` or `abspath(ACertainImportedPackage, args::String...)` that `target_path = SmallDatasetMaker.abspath(...)`.
