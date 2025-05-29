```
log_iteration(::Scheduler, method_name, obj_old, new_sol, new_incumbent, in_any_case,
    log_info)
```

Writes iteration log info.

A line is written if in*any*case is set or in dependence of `params.lfreq` and `params.lnewinc`. `method_name`: name of applied method or "-" (if initially given solution); `obj_old`: objective value before applying last operator; `param new_sol`: newly created solution; `new_incumbent`: true if the method yielded a new incumbent solution; `in_any_case`: turns filtering of iteration logs off; `log_info`: customize log info optionally added if not ""
