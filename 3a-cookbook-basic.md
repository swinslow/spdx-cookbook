# Cookbook: Basic recipes

This set of examples focuses on understanding just the basic concepts of SPDX.

### NOTE: Creation Info sections

Every SPDX tag-value document is required to start with a "Creation Info"
section. This contains a brief set of metadata regarding the authorship of the
SPDX document itself.

For completeness, the first example below will show the complete 

## Example 1: One Package with Three Files

### Scenario

Suppose you have a project consisting of three files, one in a subdirectory, and
you want to represent this in SPDX:

```
./
└──awesome/
    ├── include/
    │   └── awesome.h
    ├── awesome.c
    └── main.c
```

At the moment, we won't worry about what information we might want to convey
about this project or these files. Let's just look at the bare minimum needed to
represent this in an SPDX document.

### SPDX model

Using SPDX concepts, you could represent this as:
* one **Package** called "awesome", representing the project; and
* three **Files** contained within that Package.

You would typically not represent the directories directly as SPDX elements.
Instead, each File element contains a `FileName` property, and the directory
paths would be included in there, relative to the Package root path.

*FIXME: consider whether to have a separate example below, where subdirectories
are represented as sub-packages*

Because we're just looking at the bare minimum, we will omit any fields that the
SPDX spec says are optional. We'll just include mandatory fields.

### SPDX document

For this first example, we will include the full SPDX document.

```
##### Document Creation Info

SPDXVersion: SPDX-2.1
DataLicense: CC0-1.0
SPDXID: SPDXRef-DOCUMENT
DocumentName: project-awesome
DocumentNamespace: https://github.com/swinslow/spdx-cookbook-example-project-awesome-v1
Creator: Tool: github.com/spdx/tools-golang/v0/builder
Created: 2019-12-06T18:17:35Z

##### Package awesome

PackageName: awesome
SPDXID: SPDXRef-Package-awesome
PackageDownloadLocation: NOASSERTION
FilesAnalyzed: true
PackageVerificationCode: 3a337211c432e780f7b60a250aa2d221a523d5ca
PackageLicenseConcluded: NOASSERTION
PackageLicenseDeclared: NOASSERTION
PackageCopyrightText: NOASSERTION

##### Files in Package awesome

FileName: ./awesome/include/awesome.h
SPDXID: SPDXRef-FileAwesomeHeader
FileChecksum: SHA1: 692d2501a184d530130e3e60fb39926baabf691f
LicenseConcluded: NOASSERTION
LicenseInfoInFile: NOASSERTION
FileCopyrightText: NOASSERTION

FileName: ./awesome/awesome.c
SPDXID: SPDXRef-FileAwesomeSource
FileChecksum: SHA1: 77dfe95918d0de93cdc17b04b7061b61650a4998
LicenseConcluded: NOASSERTION
LicenseInfoInFile: NOASSERTION
FileCopyrightText: NOASSERTION

FileName: ./awesome/main.c
SPDXID: SPDXRef-FileAwesomeSource
FileChecksum: SHA1: fbad53d51479c3eff06389fe3a6779e83529d158
LicenseConcluded: NOASSERTION
LicenseInfoInFile: NOASSERTION
FileCopyrightText: NOASSERTION
```

There's a lot to unpack here. Note the following off the bat:
* Lines beginning with `#` are comments and are not mandatory, but are included
  in this example for clarity.
* For the moment, just ignore the fields with values of `NOASSERTION`. (See 'About
  NOASSERTION' section below for more details.)

### FIXME ADD CONTENT

*explain non-NOASSERTION sections and lines from above example*

### About NOASSERTION

*finish and clarify the following*

Those fields are mandatory under the v2.1 SPDX spec, so they are required to be
present in the document. Since we are ignoring data such as license info for
this example, we will just proceed with having them marked as `NOASSERTION`
(meaning, basically, that the )
