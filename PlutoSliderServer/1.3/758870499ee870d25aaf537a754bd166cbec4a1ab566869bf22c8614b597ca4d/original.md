```
run_git_directory(start_dir::String="."; export_options...)
```

Like [`run_directory`](@ref), but will automatically keep running `git pull` in `start_dir` and update the slider server to match changes in the directory. See our README for more info.

If you use a `PlutoDeployment.toml` file, we also keep checking whether this file changed. If it changed, we **exit Julia session**, and you will have to restart it. Open an issue if this is a problem.
