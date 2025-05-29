autoexogenize!(plan, model, date)

Modify the given plan according to the "autoexogenize" protocol defined in the given model. All variables in the autoexogenization list become endogenous and their corresponding shocks become exogenous over the given date or range. `date` can be a moment in time (same frequency as the given plan), a range, an iterable, or a container.
