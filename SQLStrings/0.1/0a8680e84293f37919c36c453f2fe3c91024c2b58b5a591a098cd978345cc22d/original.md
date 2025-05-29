```
sql`SOME SQL ... $var`
sql`SOME SQL ... $(var...)`
sql`SOME SQL ... 'A $literal string'`
sql``
```

The `@sql_cmd` macro is a tool for tracking SQL query strings together with their parameters, but without interpolating the parameters into the query string directly. Instead, interpolations like `$x` will result in the value of `x` being passed as a query parameter. If you've got a collection of values to interpolate into a comma separated context you can also use splatting syntax within the interpolation, for example `insert into foo values($(x...))`.

Use this rather than direct string interpolation to prevent SQL injection attacks and allow systematic conversion of Julia types into their SQL equivalents via the database layer, rather than via `string()`.

Empty query fragments can be generated with ```sql`` ``` which is useful if you must dynamically generate SQL code based on conditionals. However you should also consider embedding any conditionals on the SQL side rather than in the Julia code.

*Interpolations are ignored* inside standard SQL Strings with a single quote, so using `'A $literal string'` will include `$literal` rather than the value of the variable `literal`. If converting code from using raw strings, you may have needed to quote interpolations. In that case you can check your conversion by setting `SQLStrings.allow_dollars_in_strings[] = false`.

If you need to include a literal `$` in the SQL code outside a string, you can escape it with `\$`.
