```
MachOSegmentCmd
```

Mach-O Segment load command type, containing information about the virtual memory layout of a chunk of the program.  This type is very MachO-specific, so it is not comparable to other object file formats directly.  However, note that this data structure is the gateway through which the file sections are accessed, and while there is a convenience `Sections(::MachOHandle)` method that will abstract all that away for you, you can also directly call `Sections(::MachOLoadCmdRef{MachOSegmentCmd})` to get the sections belonging to the given segment.  Note that the `Sections` call works only upon a `MachOLoadCmdRef{MachOSegmentCmd}`, it will not work on the `MachOSegmentCmd` itself directly.

### Creation:

  * MachOSegmentCmd()

### Format-specific properties:

  * segment_name()
  * segment_offset()
  * segment*file*size()
  * segment*memory*size()
  * segment*num*sections()
