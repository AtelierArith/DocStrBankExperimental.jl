```
package(directory; [submission_dir, force_overwrite])
```

Package up the LaTeX project in `directory` to be submitted. This will find the root document and merge all embedded (via `\input`/`\include`) `tex` files into a single  file. Changes all figure references (via `\includegraphics`) to remove all nested directories and just point at the filename. Copies all figures from referenced  locations into the `submission_dir`, removing all nested folders. Writes the merged  file into the `submission_dir`. Then compiles the newly merged code using `latexmk`, and cleans up afterwards, leaving the `.bbl` file behind.

## Optional Keyword Arguments:

  * `submission_dir`: By default is set to `directory/submission`. This is the folder where submission files are copied. **DO NOT** set this to be equal to `directory`.
  * `force_overwrite`: Deletes all existing files in the `submission_dir` without asking.
