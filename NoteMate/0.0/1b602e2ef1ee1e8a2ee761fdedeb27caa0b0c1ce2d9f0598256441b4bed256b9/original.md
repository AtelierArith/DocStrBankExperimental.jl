```
generate_note_summary
```

Generate a note summary section using note title, publishing date, rss summary and any keywords.

# Arguments

  * `note`: a `FranklinNote` struct whose information is formated for the note summary section

# Return

  * a string formated according to the Open Knowledge Model standard for Franklin, starting with a note title, followed by the Date in `monthname day year` form, the RSS summary of the note, and comma-separated keywords for the note.

An example formating: 

```
Example title:
=========

**Date:** May 12 2020

**Summary:** This is the summary of an example note

**Keywords:** example files, demonstration, documentation
```
