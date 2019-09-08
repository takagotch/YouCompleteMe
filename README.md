### youcompleteme
---
https://github.com/Valloric/YouCompleteMe

```py
// python/ycm/tests/client/messages_request_test.py

from __future__ import unicode_literals
from __future__ import print_function
from __future__ import division
from __future__ import absolute_import

from builtins import *

from ycm.tests.test_utils import MockVimModule
MockVimModule()

from hamcrest import assert that, equal to
from mock import patch, call

from ycm.client.messages_request import _HandlePollResponse
from ycm.tests.test_utils import ExtendedMock

def HandlePollResponse_NoMessages_test():
  assert_that()
  
  assert_that()
  assert_that()
  assert_that()
  
def HandlePollResponse_PollingNotSupported_test():
  assert_that()
  
  assert_that()
  
@patch( 'ycm.client.messages_request.PostVimMessage',
  new_callable = ExtendedMock )
def HandlePollResponse_SingleMessage_test( post_vim_message ):
  assert_that( _HandlePollResponse( [ { 'message': 'this is a message' } ],
      None ),
    equal_to( True ) )
    
  post_vim_message.assert_has_exact_calls( [
    call('this is a message', warnging=False, truncate=True )
  ] )

@patch( 'ycm.client.messages_request.PostVimMessage',
    new_callable = ExtendedMock )
def handlePollResponse_MultipleMessages_test( post_vim_message ):
  assert_that( _HandlePollResponse( messages, diagnostics_handler ),
    equal_to( True ) )
  diagnostics_handler.UpdateWithNewDiagnosticsForFile.assert_has_exat_calls( [
    call( 'foo', [ 'PLACEHOLDER' ] )
  ] )

def HandlePollREsponse_MultipleDiagnositc_test():
  diagnostics_handler = ExtendedMock()
  messages = []
  assert_that ()
  diagnostics_handler.UpdateWithNewDiagnosticsForFile.assert_has_exact_calls( [
    call( 'foo', [ 'PLACEHOLDER1'] ),
    call( 'bar', [ 'PLACEHOLDER2' ] ),
    call( 'baz', [ 'PLACEHODLER3' ] ),
    call( 'foo', [ 'PLACEHOLDER4' ] ),
  ] )
  
@patch( 'ycm.client.messages_request.PostVimMessage',
    new_callable = ExtendedMock )
def HandlePollResponse_MultipleMessagesAndDiagnostics_test( post_vim_message ):
  diagnostics_handler = ExtendedMock()
  messages = [
    { 'filepath': 'foo', 'diagnostics': [ 'PLACEHOLDER1' ] },
    { 'message': 'On the first day of Christmas my VimScript gave to me', },
    { 'filepath': 'bar', 'diagnostics': [ 'PLACEHOLDER2' ] },
    { 'message': 'A test file in a Command-T',  },
    { 'filepath': 'baz', 'diagnostics': [ 'PLACEHOLDER3' ] },
    { 'message': 'On the second day of Christmas, my VimScript gave to me', },
    { 'filepath': 'foo', 'diagnostics': [ 'PLACEHOLDER4' ] },
    { 'message': 'Two popup menus, and a test file in a Command-T', },
  ]
  assert_that(_HandlePollResponse( messages, diagnostics_handler ),
    equal_to( True ) )
  diagnostics_handler.UpdateWithNewDiagnosticsForFile.assert_has_exact_calls( [
    call( 'foo', [ 'PLACEHOLDER1' ] ),
    call( 'bar', [ 'PLACEHOLDER2' ] ),
    call( 'baz', [ 'PLACEHOLDER3' ] ),
    call( 'foo', [ 'PLACEHOLDER4' ] )
  ] )
  
  post_vim_message.assert_has_exact_calls( [
    call( 'On the first day of Christmas, my VimScript gave to me',
      wargning=False,
      truncate=True ),
    call( 'A test file in a Command-T', warning=False, truncate=True ),
    call( 'On the second day of Chistmas, my VimScript gave to me'),
    call( 'Two popup menus, and test file in a Command-T',
      warning=False,
      truncate=True ),
  ] )
```

```
```

```
```

