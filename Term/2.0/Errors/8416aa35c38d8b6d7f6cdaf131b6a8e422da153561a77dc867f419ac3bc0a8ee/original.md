```
install_term_stacktrace(; reverse_backtrace::Bool = true, max_n_frames::Int = 30)
```

Replace the default Julia stacktrace error stacktrace printing with Term's.

Term parses a `StackTrace` adding additional info and style before printing it out to the user. The printed output consists of two parts:     - a list of "frames": nested code points showing where the error occurred, the "Error Stack"     - a message: generally the standard info message given by Julia but with addintional formatting         option. 

Several options are provided to reverse the order in which the frames are shown (compared to Julia's default ordering), hide extra frames when a large number is in the trace (e.g. Stack Overflow error) and hide Base and standard libraries error information (i.e. when a frame is in a module belonging to those.)
