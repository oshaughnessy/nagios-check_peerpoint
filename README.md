nagios-check_peerpoint
======================

Nagios plugin to check for known registrations on a PeerPoint C100
Session Border Controller


## Usage

    check_peerpoint [<flags>] -H peerpoint_host [-c contact_uri] [-r registered_host] [-i ssh_identity] [-u ssh_username] [-v]
    check_peerpoint --help
    check_peerpoint --man
    check_peerpoint --version

    Options:
      --contact|c    Contact URI to search for in the list of registered users
                     (default is "sip:nagios@" followed by the hostname param).
      --hostname|H   Hostname or IP of the PeerPoint to be checked.
      --identity|i   ssh identity file for connecting to the PeerPoint
                     (should have an empty passphrase;
                     default /etc/nagios3/ssh/id_dsa_open).
      --user|u       ssh username for connecting to the PeerPoint
                     (should have a "reader" account on the C100; default nagios).
      --registered|r Hostname or IP that will be searched for in the registration
                     (default is the Nagios server hostname).  If set to the
                     empty string, all registered clients will be returned.
      --list         List mode:  show all registered clients and their expirations
      --master       Failover mode:  show whether the given server is the
                     failover master (state OK), standby (state WARNING), or
                     is never configured to be either (state UNKNOWN)
      --verbose|v    Show details of progress (give more than once for more info).
      --help         Show this usage text.
      --man          Show the comprehensive documentation.
      --version      Show the version (0.1.7).

      This script will search the list of registered contacts on the named
      PeerPoint C100 Session Border Controller.  If the hostname or IP given
      in the "registered" option is found in the listings that match the given
      "contact" option, then the script returns success.  If no matches are
      found, the script returns failure.
