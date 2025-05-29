```
CompatHelper(;
    file="~/.julia/packages/PkgTemplates/MepaC/templates/github/workflows/CompatHelper.yml",
    destination="CompatHelper.yml",
    cron="0 0 * * *",
)
```

Integrates your packages with [CompatHelper](https://github.com/bcbi/CompatHelper.jl) via GitHub Actions.

## Keyword Arguments

  * `file::AbstractString`: Template file for the workflow file.
  * `destination::AbstractString`: Destination of the workflow file, relative to `.github/workflows`.
  * `cron::AbstractString`: Cron expression for the schedule interval.
