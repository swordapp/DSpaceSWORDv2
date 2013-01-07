DSpace SWORDv2 Enhanced Implementation
======================================

This code is intended as a replacement for the default SWORDv2 implementation that ships with DSpace version 1.8.2 and 3.0.  It is derived from that original codebase, but incorporates bugfixes, overall enhancements, and further points of configuration.

Installation
------------

The code should just be placed inside your DSpace source tree in replacement of the existing dspace-swordv2 module, and the configuraiton file should be placed in dspace/config/modules/, replacing the existing version.

Be sure to read the documentation in-line in the new configuration file, and update the values appropriately before deploying.

###METS Ingester

If you plan to use the METS ingester, you should replace the DSpaceMETSIngester in the PackageIngester part of the dspace.cfg file with the SwordMETSPackageIngester, so it should look as follows:

    plugin.named.org.dspace.content.packager.PackageIngester = \
      org.dspace.content.packager.DSpaceAIPIngester = AIP, \
      org.dspace.content.packager.PDFPackager  = Adobe PDF, PDF, \
      org.dspace.sword2.SwordMETSPackageIngester = METS, \
      org.dspace.content.packager.RoleIngester = DSPACE-ROLES

This is critically important, otherwise the METS import will fail with an error.
