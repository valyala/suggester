Suggester - the heart for full-text auto-complete web services
=========

Features
--------

  * Supports full-text prefix search.
  * It is fast. Up to 10K lookups per second for a million of keywords.
  * Low memory usage. Requires less than 100MB of RAM for a million of typical
    keywords.
  * Easy-to-hack concise source code.

Usage
-----

```
$ ipython -i ./suggester.py
In [1]: s = Suggester()
In [2]: s.update_keywords(('keyword %d' % i, 'payload %d' % i) for i in range(100000))
In [3]: s.suggest_keywords('keyword')
Out[3]: 
[(u'keyword 0', u'payload 0'),
 (u'keyword 1', u'payload 1'),
 (u'keyword 2', u'payload 2'),
 (u'keyword 3', u'payload 3'),
 (u'keyword 4', u'payload 4'),
 (u'keyword 5', u'payload 5'),
 (u'keyword 6', u'payload 6'),
 (u'keyword 7', u'payload 7'),
 (u'keyword 8', u'payload 8'),
 (u'keyword 9', u'payload 9')]

In [4]: s.suggest_keywords('123')
Out[4]: 
[(u'keyword 123', u'payload 123'),
 (u'keyword 1230', u'payload 1230'),
 (u'keyword 12300', u'payload 12300'),
 (u'keyword 12301', u'payload 12301'),
 (u'keyword 12302', u'payload 12302'),
 (u'keyword 12303', u'payload 12303'),
 (u'keyword 12304', u'payload 12304'),
 (u'keyword 12305', u'payload 12305'),
 (u'keyword 12306', u'payload 12306'),
 (u'keyword 12307', u'payload 12307')]

In [5]: s.suggest_keywords('123 key')
Out[5]: 
[(u'keyword 123', u'payload 123'),
 (u'keyword 1230', u'payload 1230'),
 (u'keyword 12300', u'payload 12300'),
 (u'keyword 12301', u'payload 12301'),
 (u'keyword 12302', u'payload 12302'),
 (u'keyword 12303', u'payload 12303'),
 (u'keyword 12304', u'payload 12304'),
 (u'keyword 12305', u'payload 12305'),
 (u'keyword 12306', u'payload 12306'),
 (u'keyword 12307', u'payload 12307')]

In [6]: s.suggest_keywords('123 foobar')
Out[6]: []

```

