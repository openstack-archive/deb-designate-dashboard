===============================
designatedashboard
===============================

Designate Horizon UI bits

* Free software: Apache license

Features
--------

* TODO


Howto
-----

1. Package the designatedashboard by running::

    python setup.py sdist

   This will create a python egg in the dist folder, which can be used to install
   on the horizon machine or within horizon's  python virtual environment.

   -- or --

   Install directly from source by running "python setup.py --install"

   Note:  On some systems python may throw an error like

      'Exception: Versioning for this project requires either an sdist tarball, or access 
       to an upstream git repository'

   this seems to be a result of mismatched pbr versioning.  A hacking workaround for development
   purposes is replacing the pbr call with a hard-coded version (e.g. '1.0.1') in
   designatedashboard/__init__.py.

2. Copy panel plugin files into your Horizon config.  These files can be found in designatedashboard/enabled
   and should be copied to /usr/share/openstack-dashboard/openstack_dashboard/local/enabled or the
   equivalent directory for your openstack-dashboard install.

3. Make sure your keystone catalog contains endpoints for service type 'dns'.  If no such endpoints are
   found, the designatedashboard panels will not render.

4. (Optional) Copy the designate policy file into horizon's policy files folder, and add this config::

    'dns': 'designate_policy.json',

5. (Optional) Within your horizon settings file(s) (either the local settings or the other settings.py), add
   the line below.  This will make it so the record create/update screen uses a drop down of your floating ip
   addresses instead of a free form text field::

    DESIGNATE = { 'records_use_fips': True }
