`PY-STRAWPOLL <https://github.com/vaibhav-y/py-strawpoll>`__
============================================================

Python wrapper for `Strawpoll's
API <https://github.com/strawpoll/strawpoll/wiki/API>`__. Provides
methods for reading from and writing to strawpoll via its JSON api.

About
-----

py-strawpoll provides the following:

``StrawpollAPIReader`` class containing methods:

-  ``from_json(string)``: Read a strawpoll into memory from its JSON
   representation
-  ``from_url(url)``: Read a strawpoll into memory from it's URL (uses
   API endpoint to fetch)
-  ``from_apiv2(poll_id)``: Read a strawpoll into memory via it's poll
   id (uses API endpoint to fetch)
-  ``total_votes()``
-  ``normalize()``: Normalize a poll to the [0, 1] range
-  ``votes_for(option_string)``: Get the raw count of votes for a
   specific option string
-  ``normalized_votes_for(option_string)``: Get the normalized votes for
   a specific option string
-  ``winner()``: Who won the poll?
-  ``loser()``: Least favoured option
-  ``to_clean_dict()``: Returns a python dictionary representation of
   the poll. Ignores any atributes that are null

Usage
-----

Installation
~~~~~~~~~~~~

-  TODO: Create a PyPI package

Fetching a strawpoll
~~~~~~~~~~~~~~~~~~~~

.. code:: python

    from strawpoll import StrawpollAPIReader

    json_string = '{
      "title":"What movie should we watch again?",
      "options":  [
        "Sucker punch ",
        "Pirates of carribian ",
        "Prison logic","Witchhunter"
      ],
      "multi":false,
      "permissive": false,
      "captcha": true
    }'

    # Fetch a poll through its API id
    poll_a = StrawpollAPIReader.from_apiv2(1)

    # Fetch a poll through its URL
    poll_b = StrawpollAPIReader.from_url("https://strawpoll.me/1")

    # Fetch a poll from its JSON dump
    poll_c = StrawpollAPIReader.from_json(json_string)

    # These should be the same
    if (poll_a == poll_b) and (poll_b == poll_c):
      print "Mirror images!"

    # Yada yada normalize your data
    print poll_a.normalize()

Posting a strawpoll
~~~~~~~~~~~~~~~~~~~

-  TODO: APIWriter still in the pipes

Changelog
---------

`CHANGES.txt <./CHANGES.txt>`__
