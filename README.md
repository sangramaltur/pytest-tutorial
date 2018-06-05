# pytest-tutorial
Teaching myself Pytest


- Pytest file should start with "test" as prefix as it uses it as an identifier
- Functions should start with test as prefix
- Pytest runs recursively trying to identify all the files / functions with test as prefix

- Different ways to run pytest
  - $ python -m pytest
  - $ pytest -q
  - $ pytest -v

- Skip tests
  - Add a decorator above the test funciton to skip it"@pytest.mark.skip(reason="dont want to run this test")"
  - Can use skipif for condition check "@pytest.mark.skipif(sys.version_info < (3, 5), reason="dont want to run this test")"
  - pytest -v rxs [prints the reson why a particular test was skipped ]

- Selectively run tests using their name
  - pytest -k multiply -v [ runs only tests with multiply as part of the name ]

- Custom markers
  - @pytest.mark.mac / @pytest.mark.windows [ add markers above func based on a name like mac/windows]
  - $ pytest -m mac -v / $ pytest -m windows -v [ run the tests only with custom markers mac/Windows]
  - $ pytest -m "not mac" -v / $ pytest -m "not windows" -v [ run all the tests other than custom markers mac/windows]

- Pytest fixtures
  - Setup and teardown conections
  - @pytest.fixture declare the decorator above a function to setup and tear down the connection
  - $ pytest -v --capture=no test_mydb.py , will print the output of print on stdout
  - @pytest.fixture(scope="module") , will setup the connection only once at the module level
  - yield curs , used to tearn down the connections after tests complete .

- Parameterise the inputs and outputs
  - Can pass input and expected output and run for multiple values
  - @pytest.mark.parametrize("test_input, expected_output",
                         [
                             (5, 25),
                             (9, 81),
                             (10, 100),
                         ]
                         )

